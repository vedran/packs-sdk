---
nav: {{name}}
description: {{description}}
{{#if icon}}icon: {{icon}}{{/if}}
{{#if tags}}tags: {{{toJson tags}}}{{/if}}
---

# {{pageTitle this}}

{{{content}}}

{{#if (isTopic this)}}
{{! Topic Sample }}

{{#if learnMoreLink}}
[Learn More](../../..{{learnMoreLink}}){ .md-button }
{{/if}}

{{#each exampleSnippets}}
## {{name}}
{{content}}

```ts
{{{code}}}
```
{{/each}}

{{else}}

{{! Full Sample }}
{{#each exampleSnippets}}
=== "{{name}}"
    ```ts
    {{{indent code 4}}}
    ```
{{/each}}

{{/if}}
