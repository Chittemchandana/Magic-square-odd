# Magic-square-odd
// C++ program to generate odd sized magic squares
#include <bits/stdc++.h>
using namespace std;

// A function to generate odd sized magic squares
void generateSquare(int n)
{
	int magicSquare[n][n];

	// set all slots as 0
	memset(magicSquare, 0, sizeof(magicSquare));

	// Initialize position for 1
	int i = n / 2;
	int j = n - 1;

	// One by one put all values in magic square
	for (int num = 1; num <= n * n;) {
		if (i == -1 && j == n) // 3rd condition
		{
			j = n - 2;
			i = 0;
		}
		else {
			// 1st condition helper if next number
			// goes to out of square's right side
			if (j == n)
				j = 0;

			// 1st condition helper if next number
			// is goes to out of square's upper side
			if (i < 0)
				i = n - 1;
		}
		if (magicSquare[i][j]) // 2nd condition
		{
			j -= 2;
			i++;
			continue;
		}
		else
			magicSquare[i][j] = num++; // set number

		j++;
		i--; // 1st condition
	}

	// Print magic square
	cout << "The Magic Square for n=" << n
		<< ":\nSum of "
			"each row or column "
		<< n * (n * n + 1) / 2 << ":\n\n";
	for (i = 0; i < n; i++) {
		for (j = 0; j < n; j++)

			// setw(7) is used so that the matrix gets
			// printed in a proper square fashion.
			cout << setw(4) << magicSquare[i][j] << " ";
		cout << endl;
	}
}

// Driver code
int main()
{

	// Works only when n is odd
	int n = 7;
	generateSquare(n);
	return 0;
}

# Vedic Mathematics Approach:
# approach2
#include <bits/stdc++.h>
using namespace std;

int main() {
int n = 7;
// Make vector to store numbers of square
vector<vector<int>> magicSquare(n, vector<int>(n, -1));
// Indices for element to be inserted
int x = (n / 2), y = n - 1;
// Loop till n ^ 2 times
for(int i=1; i<=n*n; i++) {
	// Put the current element at (x, y)
	magicSquare[x][y] = i;
	
	if(i % n == 0) {
	// If we get multiple of n, move left
	y--;
	} else {
	// Else, move top-right 
	x--; y++;
	}
	// Take modulo to avoid out of bounds
	x += n; x %= n;
	y += n; y %= n;
}

// Print magic square
for(int i=0; i<n; i++) {
	for(int j=0; j<n; j++) {
	cout<< magicSquare[i][j]<< " ";
	}
	cout<< endl;
}

return 0;
}

