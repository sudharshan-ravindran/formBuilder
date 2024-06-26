# typeUserEvents
Add functionality to existing and custom attributes using `onclone` and `onadd` events. Events return JavaScript DOM elements.

For all types the wildcard type **_*_** exists.

`onremove` event exists for removal events

## Usage
```javascript
var options = {
  dataType: 'json',
  typeUserAttrs: {
    text: {
      pattern: {
        label: 'Pattern',
        description: 'Enter a RegExp passwords must match'
      }
    }
  },
  typeUserEvents: {
    '*': {
      onclone: (fld) => {
        console.log('field cloned');
      }
    },
    text: {
      onadd: function(fld) {
        var $patternField = $('.fld-pattern', fld);
        $patternField.prop('disabled', true).parent().hide();
        $('.fld-subtype', fld)
          .change(function(e) {
            var toggle = (e.target.value === 'password');
            $patternField.prop('disabled', !toggle).parent().toggle(toggle);
          });
      }
    }
  }
};
$(container).formBuilder(options);
```
<p data-height="525" data-embed-version="2" data-theme-id="22927" data-slug-hash="Egmrwy" data-default-tab="js,result" data-user="sudharshan" class="codepen"></p>
