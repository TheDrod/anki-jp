<div class="card-container">

  <!-- FRONT TEMPLATE -->
  <div class="front-container">
    <div class="question-wrapper">
      <span class="word">{{furigana::Reading}}</span>
      <span class="tags">{{Tags}}</span>
    </div>
    {{#Audio}}<div class="audio">{{Audio}}</div>{{/Audio}}
  </div>

  <!-- BACK TEMPLATE -->
  <div class="back-container">
    <div class="answer-wrapper">
      <span class="answer">{{furigana::Meaning}}</span>
      {{#Meaning__Extra}}
      <span class="answer-extra">{{furigana::Meaning__Extra}}</span>
      {{/Meaning__Extra}}
    </div>

    <div class="extra-container">
      {{#Example}}
      <div class="extra-container-wrapper">
        <span class="title">Example</span>
        <div class="info-wrapper example1 toggler">
          <span class="expression">{{kanji::Example}}</span>
          <span class="furigana hidden">{{furigana::Example}}</span>
          {{#Example__Meaning}}
          <span class="meaning hidden">{{Example__Meaning}}</span>
          {{/Example__Meaning}}
        </div>
        {{#Example_2}}
        <div class="info-wrapper example2 toggler">
          <span class="expression">{{kanji::Example_2}}</span>
          <span class="furigana hidden">{{furigana::Example_2}}</span>
          {{#Example_2__Meaning}}
          <span class="meaning hidden">{{Example_2__Meaning}}</span>
          {{/Example_2__Meaning}}
        </div>
        {{/Example_2}}
      </div>
      {{/Example}}

      <div class="separator"></div>

      {{#vParticles}}
      <div class="extra-container-wrapper">
        <span class="title">Particles</span>
        <span class="info">{{furigana::vParticles}}</span>
      </div>
      {{/vParticles}}

      <div class="separator"></div>

      {{#vGroup}}
      <div class="extra-container-wrapper">
        <div><span class="title">Verb Group</span>: <span>{{vGroup}}</span></div>
        {{#vForm_て}}<span class="info">Form -て: {{furigana:vForm_て}}</span>{{/vForm_て}}
        {{#vForm_い}}<span class="info">Form -い: {{furigana:vForm_い}}</span>{{/vForm_い}}
      </div>
      {{/vGroup}}

      <div class="separator"></div>

      {{#Notes}}
      <div class="extra-container-wrapper">
        <span class="title">Notes</span>
        <span class="info">{{furigana::Notes}}</span>
      </div>
      {{/Notes}}

      <div class="separator"></div>

      {{#Image}}
      <div class="extra-container-wrapper image-wrapper">
        <div class="image">{{Image}}</div>
      </div>
      {{/Image}}
    </div>

    <div class="hyperlink-resources">
      <a class="link" href="http://jisho.org/words?jap={{Expression}}">Jisho</a>
      <!-- <a class="link" href="http://ejje.weblio.jp/content/{{Expression}}">Weblio</a> -->
      <a class="link" href=https://www.japandict.com/{{Expression}}?lang=eng">JapanDict</a>
      <!-- <a class="link" href="http://dictionary.goo.ne.jp/srch/all/{{Expression}}/m0u/">goo</a> -->
      <!-- <a class="link" href="http://eow.alc.co.jp/search?q={{Expression}}&ref=sa">ALC</a> -->
    </div>
  </div>
</div>

<!-- ----------------------------------------------------------------- -->
<!-- ----------------------------------------------------------------- -->
<script>
  const modes = {
    'kanji': 'furigana',
    'furigana': 'kanji',
  };

  const handleMode = function () {
    let expression = null;
    let furigana = null;
    let meaning = null;

    this.childNodes.forEach(child => {
      if (child.nodeName !== 'SPAN') return;

      if (child.classList.contains('expression')) {
        expression = child;
        return;
      }
      if (child.classList.contains('furigana')) {
        furigana = child;
        return;
      }
      if (child.classList.contains('meaning')) {
        meaning = child;
        return;
      }
    });

    const currentMode = this.classList.contains('furigana') ? 'furigana' : 'kanji';
    const newMode = modes[currentMode];

    this.classList.remove(currentMode);
    this.classList.add(newMode);

    if (newMode === 'kanji') {
      expression.classList.remove('hidden');
      furigana.classList.add('hidden');
      if (meaning !== null) {
        meaning.classList.add('hidden');
      }
    } else {
      expression.classList.add('hidden');
      furigana.classList.remove('hidden');
      if (meaning !== null) {
        meaning.classList.remove('hidden');
      }
    }
  };

  // TODO: use instead of single .example1 and .example2
  // const togglers = document.querySelectorAll('.toggler');

  const example1 = document.querySelector('.example1');
  const example2 = document.querySelector('.example2');

  example1.onclick = handleMode;
  example2.onclick = handleMode;
</script>