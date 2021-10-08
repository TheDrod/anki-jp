<div class="card-container">

  <!-- Recognition Card -->
  {{^isAudioCard}}
  {{^isProduceCard}}
    <div class="front-container recognition">
      <div class="quest-wrapper">
        <span class="quest">Recognition</span>
      </div>
      <div class="question-wrapper toggler">
        <span class="expression">{{kanji::Reading}}</span>
        <span class="furigana hidden">{{furigana::Reading}}</span>
        <span class="tags hidden">{{Tags}}</span>
      </div>
      {{#Audio}}<div class="audio">{{Audio}}</div>{{/Audio}}
    </div>
  </div>
  {{/isProduceCard}}
  {{/isAudioCard}}

  <!-- Produce Card -->
  {{^isAudioCard}}
  {{#isProduceCard}}
  <div class="front-container production">
    <div class="quest-wrapper">
      <span class="quest">Produce</span>
    </div>
    <div class="question-wrapper phrase">
      <div class="meaning">{{Meaning}}</div>
      <span class="tags">{{Tags}}</span>
    </div>
  </div>
  {{/isProduceCard}}
  {{/isAudioCard}}

  <!-- Audio Card -->
  {{#isAudioCard}}
  <div class="front-container listening">
    <div class="quest-wrapper">
      <span class="quest">Listening</span>
    </div>
    <div class="question-wrapper">
      <div class="">{{Audio}}</div>
      <span class="tags">{{Tags}}</span>
    </div>
  </div>
  {{/isAudioCard}}

</div>

<!-- ----------------------------------------------------------------- -->
<!-- ----------------------------------------------------------------- -->
<script>
  const toggler = document.querySelector('.toggler');
  const expression = document.querySelector('.expression');
  const furigana = document.querySelector('.furigana');
  const quest = document.querySelector('.quest');
  const tags = document.querySelector('.tags');

  const modes = {
    'kanji': 'furigana',
    'furigana': 'kanji',
  };

  toggler.onclick = function () {
    const currentMode = this.classList.contains('furigana') ? 'furigana' : 'kanji';
    const newMode = modes[currentMode];

    this.classList.remove(currentMode);
    this.classList.add(newMode);

    if (newMode === 'kanji') {
      expression.classList.remove('hidden');
      furigana.classList.add('hidden');
      tags.classList.add('hidden');
    } else {
      expression.classList.add('hidden');
      furigana.classList.remove('hidden');
      tags.classList.remove('hidden');
    }
  }
</script>