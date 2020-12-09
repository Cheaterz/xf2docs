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

## Custom ajax
When you use third-party scripts (like rater.js, for example), you can get into a situation, when the script itself handles the ajax calls. Thus, you should manually pass some parameters and, more important, show overlay if needed.

You MUST pass csrf tokem and, if you want to show correct overlay, the _xfResponseType param:
```
additional_data: {_xfToken: `${XF.config.csrf}`, _xfResponseType: 'json', _xfWithData: 1,}
```

## Custom overlay
And this is how you can build the correct overlay from the custom ajax response:
```
// some code
success: function(response) {
    let overlay = XF.getOverlayHtml({html: data.html.content, title: data.html.title});
    XF.showOverlay(overlay);
}
```