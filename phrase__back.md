<div class="card-container">

  <!-- FRONT TEMPLATE -->
  <div class="front-container">
    <div class="question-wrapper phrase">
      <span class="">{{furigana::Reading}}</span>
      <span class="tags">{{Tags}}</span>
    </div>
    {{#Audio}}<div class="audio">{{Audio}}</div>{{/Audio}}
  </div>

  <!-- BACK TEMPLATE -->
  <div class="back-container">
    <div class="answer-wrapper">
      <span class="answer phrase">{{furigana::Meaning}}</span>
      {{#Meaning__Extra}}
      <span class="answer-extra">{{furigana::Meaning__Extra}}</span>
      {{/Meaning__Extra}}
    </div>

    <div class="extra-container">
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
  </div>
</div>