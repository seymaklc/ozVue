<template>
  <div>
  <div class = "row">
    <div class="col">
      <card>
        <div class="toggle-switch">
<!--          <div class="row-12">-->
            <span class="label">Use Graphlet Guided Network (GGN)</span>
            <label class="switch">
              <input type="checkbox" v-model="toggleValue" @change="toggleSwitch" />
              <span class="slider"></span>
            </label>
<!--          </div>-->
        </div>
        </card>
    </div>
      <div class="col">
        <card>
<!--        <div class="integer-input">-->
<!--          <div class="integer-heading">Maximum Interaction Count: </div>-->
<!--          <input type="number" v-model.number="integerValue" min = "0" />-->
<!--        </div>-->
          <div class="integer-input">
            <label class="integer-label">Max Interaction Count:</label>
            <input class="integer-textbox" type="number" v-model.number="integerValue" min="0" />
          </div>
      </card>
      </div>
    </div>

  <div class="row">
    <div class="col">
        <card>
          <div class="slide-bar">
            <div class="slider-heading">Damping Factor * </div>
<!--            <span class="label">Slide Bar 1:</span>-->
              <input
                type="range"
                v-model="slideBarValue1"
                min="0"
                max="1"
                step="0.025"
                @input="updateSlideBarValue1"
              />
            <span class="value">{{ slideBarValue1 }}</span>
          </div>
    </card>
    </div>

    <div class="col">
      <card>
        <div class="slide-bar">
          <span class="label">Scaling Factor *</span>
          <input
            type="range"
            v-model="slideBarValue2"
            min="0"
            max="1"
            step="0.025"
            @input="updateSlideBarValue2"
          />
          <span class="value">{{ slideBarValue2 }}</span>
        </div>
      </card>
    </div>
  </div>
  </div>
</template>


<!--<template>-->
<!--  <div class="row">-->
<!--    <div class="col-md-12">-->
<!--      <card>-->
<!--        <template slot="header">-->
<!--          <h4 class="card-title">Paper Dashboard Headings</h4>-->
<!--          <p class="card-category">-->
<!--            Created using-->
<!--            <a href="https://www.google.com/fonts/specimen/Muli">Muli</a> Font-->
<!--            Family-->
<!--          </p>-->
<!--        </template>-->
<!--        <div class="content">-->
<!--          <div class="typo-line">-->
<!--            <h1>-->
<!--              <p class="category">Header 1</p>-->
<!--              Paper Dashboard Heading-->
<!--            </h1>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <h2>-->
<!--              <p class="category">Header 2</p>-->
<!--              Paper Dashboard Heading-->
<!--            </h2>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <h3>-->
<!--              <p class="category">Header 3</p>-->
<!--              Paper Dashboard Heading-->
<!--            </h3>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <h4>-->
<!--              <p class="category">Header 4</p>-->
<!--              Paper Dashboard Heading-->
<!--            </h4>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <h5>-->
<!--              <p class="category">Header 5</p>-->
<!--              Paper Dashboard Heading-->
<!--            </h5>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <h6>-->
<!--              <p class="category">Header 6</p>-->
<!--              Paper Dashboard Heading-->
<!--            </h6>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <p>-->
<!--              <span class="category">Paragraph</span>Lorem ipsum dolor sit amet,-->
<!--              consectetuer adipiscing elit, sed diam nonummy nibh euismod-->
<!--              tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi-->
<!--              enim ad minim veniam.-->
<!--            </p>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <p class="category">Quote</p>-->
<!--            <blockquote>-->
<!--              <p>-->
<!--                Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed-->
<!--                diam nonummy nibh euismod tincidunt ut laoreet dolore magna-->
<!--                aliquam erat volutpat. Ut wisi enim ad minim veniam.-->
<!--              </p>-->
<!--              <small> Steve Jobs, CEO Apple </small>-->
<!--            </blockquote>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <p class="category">Muted Text</p>-->
<!--            <p class="text-muted">-->
<!--              Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam-->
<!--              nonummy nibh euismod tincidunt ut laoreet.-->
<!--            </p>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            &lt;!&ndash;-->
<!--               there are also "text-info", "text-success", "text-warning", "text-danger" clases for the text-->
<!--               &ndash;&gt;-->
<!--            <p class="category">Coloured Text</p>-->
<!--            <p class="text-primary">-->
<!--              Text Primary - Light Bootstrap Table Heading and complex bootstrap-->
<!--              dashboard you've ever seen on the internet.-->
<!--            </p>-->
<!--            <p class="text-info">-->
<!--              Text Info - Light Bootstrap Table Heading and complex bootstrap-->
<!--              dashboard you've ever seen on the internet.-->
<!--            </p>-->
<!--            <p class="text-success">-->
<!--              Text Success - Light Bootstrap Table Heading and complex bootstrap-->
<!--              dashboard you've ever seen on the internet.-->
<!--            </p>-->
<!--            <p class="text-warning">-->
<!--              Text Warning - Light Bootstrap Table Heading and complex bootstrap-->
<!--              dashboard you've ever seen on the internet.-->
<!--            </p>-->
<!--            <p class="text-danger">-->
<!--              Text Danger - Light Bootstrap Table Heading and complex bootstrap-->
<!--              dashboard you've ever seen on the internet.-->
<!--            </p>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <h2>-->
<!--              <p class="category">Small Tag</p>-->
<!--              Header with small subtitle-->
<!--              <br />-->
<!--              <small>".small" is a tag for the headers</small>-->
<!--            </h2>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <p class="category">Lists</p>-->
<!--            <div class="row">-->
<!--              <div class="col-md-3">-->
<!--                <h5>Unordered List</h5>-->
<!--                <ul>-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                  <li class="list-unstyled">-->
<!--                    <ul>-->
<!--                      <li>List Item</li>-->
<!--                      <li>List Item</li>-->
<!--                      <li>List Item</li>-->
<!--                    </ul>-->
<!--                  </li>-->
<!--                  <li>List Item</li>-->
<!--                </ul>-->
<!--              </div>-->
<!--              <div class="col-md-3">-->
<!--                <h5>Ordered List</h5>-->
<!--                <ol>-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                </ol>-->
<!--              </div>-->
<!--              <div class="col-md-3">-->
<!--                <h5>Unstyled List</h5>-->
<!--                <ul class="list-unstyled">-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                </ul>-->
<!--              </div>-->
<!--              <div class="col-md-3">-->
<!--                <h5>Inline List</h5>-->
<!--                <ul class="list-inline">-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                  <li>List Item</li>-->
<!--                </ul>-->
<!--              </div>-->
<!--            </div>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <p class="category">Blockquotes</p>-->
<!--            <div class="row">-->
<!--              <div class="col-md-6">-->
<!--                <h5>Default Blockquote</h5>-->
<!--                <blockquote>-->
<!--                  <p>-->
<!--                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.-->
<!--                    Integer posuere erat a ante.-->
<!--                  </p>-->
<!--                </blockquote>-->
<!--              </div>-->
<!--              <div class="col-md-6">-->
<!--                <h5>Blockquote with Citation</h5>-->
<!--                <blockquote>-->
<!--                  <p>-->
<!--                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.-->
<!--                    Integer posuere erat a ante.-->
<!--                  </p>-->
<!--                  <small-->
<!--                    >Someone famous in-->
<!--                    <cite title="Source Title">Source Title</cite>-->
<!--                  </small>-->
<!--                </blockquote>-->
<!--              </div>-->
<!--            </div>-->
<!--          </div>-->
<!--          <div class="typo-line">-->
<!--            <p class="category">Code</p>-->
<!--            <p>-->
<!--              This is-->
<!--              <code>.css-class-as-code</code>, an example of an inline code-->
<!--              element. Wrap inline code within a-->
<!--              <code> &lt;code&gt;...&lt;/code&gt;</code>tag.-->
<!--            </p>-->
<!--            <pre>-->
<!--1. #This is an example of preformatted text. 2. #Here is another line of code</pre-->
<!--            >-->
<!--          </div>-->
<!--        </div>-->
<!--      </card>-->
<!--    </div>-->
<!--  </div>-->
<!--</template>-->
<script>

export default {
  data() {
    return {
      toggleValue: false,
      slideBarValue1: 0,
      slideBarValue2: 0,
      integerValue: null,
    };
  },
  methods: {
    toggleSwitch() {
      // Handle toggle switch logic here
    },
    updateSlideBarValue1() {
      // Handle slide bar 1 value update logic here
    },
    updateSlideBarValue2() {
      // Handle slide bar 2 value update logic here
    },
  },
};
</script>

<style scoped>
/*.typography {*/
/*  padding: 20px;*/
/*}*/

.title {
  font-size: 24px;
  margin-bottom: 20px;
}

.toggle-switch{
  margin-top: 22px;
  margin-bottom: 20px;
  margin-left: 25px;
}

.slide-bar {
  margin-bottom: 20px;
}

.label {
  display: inline-block;
  width: 150px;
  /*position: center;*/
}

.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
  bottom: 15px;
  left: 60px;
  margin-left: 50px;

}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  transition: 0.4s;
  border-radius: 34px;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  transition: 0.4s;
  border-radius: 50%;
}

.switch input:checked + .slider {
  background-color: #2196f3;
}

.switch input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

.switch input:checked + .slider:before {
  transform: translateX(26px);
}

.slide-bar input[type="range"] {
  width: 100%;
}

.value {
  margin-left: 10px;
}

.integer-input {
  display: flex;
  align-items: center;
    margin-top: 10px;
    width: 300px;
    margin-bottom: 20px;
    margin-left: 30px;
}

.integer-label {
  margin-right: 100px;
  font-weight: bold;
  width: 250px;
}

.integer-textbox {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
}


/*.integer-input {*/
/*  margin-top: 10px;*/
/*  width: 60px;*/
/*  margin-bottom: 20px;*/
/*  margin-left: 30px;*/
/*}*/

/*.integer-heading {*/
/*  display: inline-block;*/
/*  width: 250px;*/
/*}*/
</style>
