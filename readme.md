# Etch

Encrypt a file, or decrypt a file and print to `stdout`

## Usage
````
Etch(1)
Encrypt a file, or decrypt a file and print to stdout.

Options:
  -e, --encrypt <file>    Encrypt file to new file <file>-aes256
  -d, --decrypt <file>    Decrypt a file and print to stdout
  -h, --help              Print this help message
````

### Encrypt a file
````
etch -e ~/secret.txt

> ~/secret.txt-aes256
````
You'll be prompted for a passphrase to encrypt the file. The encrypted data is
the written to file in the same directory as the input file, in the
case above `~/secret.txt-aes256`.

### Decrypt a file
````
etch -d ~/secret.txt-aes256

> My secret data...
````
You'll be prompted for the passphrase used to encrypt the file before the
decrypted data is printed to `stdout`.

### Convert a file
`etch` doesn't delete or overwrite any files, and has no 'conversion'
features.

You might want to do something like this to 'convert' a file:
````
etch -e secret.txt && rm secret.txt
````

To 'convert' an encrypted file, you might want to do something like this:
````
touch secret.txt && etch -d secret.txt-aes256 >> secret.txt && rm secret.txt-aes256
````

### License
MIT License
