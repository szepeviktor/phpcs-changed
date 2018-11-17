This library allows running [phpcs](https://github.com/squizlabs/PHP_CodeSniffer) on files, but only report warnings/errors from lines which were added or modified.

This library exposes a function `getNewPhpcsMessages()` which takes three arguments:

- (string) The full unified diff of a single file.
- (PhpcsMessages) The messages resulting from running phpcs on the file before your recent changes.
- (PhpcsMessages) The messages resulting from running phpcs on the file after your recent changes.

It will return an instance of PhpcsMessages which is a filtered list of the third argument above where every line that was present in the second argument has been removed.

## PhpcsMessages

This represents the output of running phpcs. You can create one from real phpcs JSON output by using `PhpcsMessages::fromPhpcsJson()`.

To read the phpcs JSON output from an instance of PhpcsMessages, you can run `$instance->toPhpcsJson()`.
