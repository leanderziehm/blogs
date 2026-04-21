# YAML

Use `|` if you want those line breaks to be preserved as `\n` (for instance, embedded markdown with paragraphs).

multi line preserving new line \n:

```yml
  key: |
    ### Heading
    * Bullet
    * Points
```

text converting new line chars to spaces in one line:&#x20;

```yml
key: >
    Your long
    string here.
```

