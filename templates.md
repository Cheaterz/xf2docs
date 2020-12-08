# Templates
Here are some template tips (some of them are listed in the official docs).

## Get CSRF-token
Here is how you can get csrf-token in javascript:
```
${XF.config.csrf}
```

e.g.:
```
// building data for ajax call
// ....
// some other code
additional_data: {_xfToken: `${XF.config.csrf}`,}
```

And this is how you can add the corresponing field to a form;
```
<xf:csrf />
```

And you can get raw token in php code:
```
\XF::app()->get('csrf.token');
```