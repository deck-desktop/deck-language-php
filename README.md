# PHP for Deck

Intelephense, for `.php` and `.phtml`. A project is anything with a `composer.json`.

```sh
npm i -g intelephense
```

Pure Node, so it needs no PHP runtime on the machine — which matters if you are editing a Laravel
project from a machine that does not run it.

## Blade templates

`foo.blade.php` works without being claimed: Deck resolves a language by the last extension, so
a Blade file is a PHP file. The PHP inside it is analysed and the directives (`@if`, `{{ }}`) are
not highlighted, because Monaco ships no Blade grammar.

## No semantic colours

Intelephense was asked for its capabilities over LSP and advertises no `semanticTokensProvider`,
so `extraTokenColors` would be inert and is deliberately absent. Colour comes from Monaco's own
PHP grammar. Everything else is there: completion, hover, go-to-definition, references, rename,
formatting and diagnostics.

## Installing it

From inside Deck: **Settings -> Plugins -> Browse**, pick it, and it loads straight away.

By hand: copy this folder into `%APPDATA%\Deck\languages\` (`Deck-Dev` for a debug build).
`docs/languages.md` in the Deck repository documents the format.

## What a definition can and cannot do

It is **data**, not code. `language.json` is parsed field by field and never executed, which is
why a language is a different kind of thing from a plugin even though both are folders Deck
reads at startup. The worst a malformed one can do is skip itself.
