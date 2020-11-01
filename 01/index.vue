<template>
  <div id="app" class="app">
    <header class="header">
      <h1 class="header__title">
        &#x1F331; Life Fullfilment Progress &#x1F331;
      </h1>
      <div class="header__info">
        <p>
          This bar below indicates how many things you have done in your life in comparison to a "basic human life". This app isn't based on any sociological or psychological research, so don't put much pressure on it. Select what have you already achieved by clicking on it and see how "full" is your life &#x1F600;. If you want to uncheck something just click once again.
        </p>
      </div>
      <div class="header__bar">
        <div
          class="header__bar_progress"
          v-bind:style="{ width: fullfilment + '%' }"
        ></div>
        <div class="header__bar_value">
          {{ fullfilment }}%
        </div>
      </div>
      <h2 class="header__sub-header">
        You...
      </h2>
    </header>
    <div class="event-selector">
      <button
        v-for="(event, index) in events"
        :key="index"
        v-on:click.prevent="eventClicked(index)"
        v-bind:class="[
          'event-selector__event',
          { 'event-selector__event--active': event.done }]"
        >
        {{ event.icon }} {{ event.name }}
      </button>
    </div>
      <footer class="footer">
    Made with ❤️ by <a target="_blank" class="footer__link" href="https://danieo.me/">Daniel Budziński</a>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
     done: 0,
     events : [
       {
         icon: '✈️',
         name: 'Flew with a plane',
         done: false,
       },
       {
         icon: '💍',
         name: 'Got married',
         done: false,
       },
       {
         icon: '🛥️',
         name: 'Swam with a boat',
         done: false,
       },
       {
         icon: '💑',
         name: 'Had a boyfriend/girlfriend',
         done: false,
       },
       {
         icon: '👶',
         name: 'Got children',
         done: false,
       },
       {
         icon: '💸',
         name: 'Got a dreamjob',
         done: false,
       },
       {
         icon: '🏫',
         name: 'Graduated from a highschool',
         done: false,
       },
       {
         icon: '🎓',
         name: 'Graduated from a university',
         done: false,
       },
       {
         icon: '💕',
         name: 'Had your first time',
         done: false,
       },
       {
         icon: '💰',
         name: 'Received first paycheck',
         done: false,
       },
       {
         icon: '💀',
         name: 'Lost someone close',
         done: false,
       },
       {
         icon: '🌊',
         name: 'Saw the ocean',
         done: false,
       },
       {
         icon: '⛰️',
         name: 'Were in the mountains',
         done: false,
       },
       {
         icon: '🔭',
         name: 'Saw celestial bodies with a telescope',
         done: false,
       },
       {
         icon: '🏠',
         name: 'Got a house',
         done: false,
       },
       {
         icon: '🌳',
         name: 'Planted a tree',
         done: false,
       },
       {
         icon: '🐕',
         name: 'Had a dog',
         done: false,
       },
       {
         icon: '🐈',
         name: 'Had a cat',
         done: false,
       },
       {
         icon: '🎃',
         name: 'Collected candies on halloween',
         done: false,
       },
       {
         icon: '🚅',
         name: 'Traveled with a train',
         done: false,
       },
       {
         icon: '🚗',
         name: 'Got drivers license',
         done: false,
       },
       {
         icon: '🥳',
         name: 'Celebrated your birthday',
         done: false,
       },
       {
         icon: '🧳',
         name: 'Went abroad',
         done: false,
       },
       {
         icon: '💏',
         name: 'Kissed someone',
         done: false,
       },
       {
         icon: '🦑',
         name: 'Ate something odd',
         done: false,
       },
       {
         icon: '🏊',
         name: 'Learned to swim',
         done: false,
       },
       {
         icon: '🚴',
         name: 'Learned to bicycle',
         done: false,
       },
              {
         icon: '🛠️',
         name: 'Made something by yourself',
         done: false,
       },
       {
         icon: '🏆',
         name: 'Won something',
         done: false,
       },
       {
         icon: '🎁',
         name: 'Received a gift that made you smile',
         done: false,
       },
       {
         icon: '🩸',
         name: 'Donated blood',
         done: false,
       },
       {
         icon: '🇬🇧',
         name: 'Learned a foreign language',
         done: false,
       },
       {
         icon: '🍎',
         name: 'Have eaten healthy',
         done: false,
       },
       {
         icon: '⚽',
         name: 'Played sports',
         done: false,
       },
     ]
    };
  },
  computed: {
    fullfilment() {
      return Math.round((this.done / this.events.length) * 100);
    }
  },
  methods: {
    incrementFullfilment() {
      this.done++;
    },
    decrementFullfilment() {
      this.done--;
    },
    eventClicked(id) {
      if (!this.events[id].done) {
        this.events[id].done = true;
        this.incrementFullfilment();
      } else {
        this.events[id].done = false;
        this.decrementFullfilment();
      }
    }
  }
};
</script>
<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Catamaran:wght@300,400&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap');

  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  html, body {
    width: 100vw;
    color: #171717;
    font-size: 18px;
    font-family: 'Catamaran', sans-serif;
    background: #fafafa;
  }

  .app {
    margin: auto;
    max-width: 1024px;
    padding: 15px;
  }

  .header {
    &__title {
      font-weight: 400;
      text-align: center;
      margin-top: 1em;
    }
  
    &__sub-header {
      margin-top: 1em;
      text-align: center;
      font-weight: 300;
    }

    &__info {
      display: flex;
      justify-content: center;
      margin-top: 1.5em;
      margin-bottom: 1em;
      & p {
        width: 70%;
        text-align: justify;
        font-weight: 300;
      }
    }

    &__bar {
      position: relative;
      height: 2em;
      margin-top: 1.5em;
      border: 1px solid #171717;
      border-radius: 5px;

      &_progress {
        position: absolute;
        top: 0;
        left: 0;
        width: 50%;
        height: 100%;
        background: #8bc34a;
        transition: 1s;
      }

      &_value {
        display: flex;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        justify-content: center;
        align-items: center;
        font-family: 'Roboto', sans-serif;
        font-weight: 500;
        font-size: 1.3em;
      }
    }
  }

  .event-selector {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: calc(100% + 15px);
    margin: calc(0.5em - 15px) 0 0 -15px;

    &__event {
      padding: 7px 15px;
      margin: 15px 0 0 15px;
      border: 1px solid #171717;
      border-radius: 5px;
      background: none;
      font-size: 1.1em;
      font-weight: 300;
      font-family: 'Catamaran', sans-serif;
      cursor: pointer;
      transition: .3s;
    }

    &__event:hover {
      background: #aed581;
    }

    &__event:active {
      background: #8bc34a;
    }

    &__event--active, &__event--active:hover {
      background: #8bc34a;
    }
  }

  .footer {
    margin-top: 1.5em;
    margin-bottom: -15px;
    width: 100%;
    text-align: center;
    font-weight: 300;

    &__link {
      font-weight: 400;
      text-decoration: none;
      color: #8bc34a;
    }

    &__link:hover {
      color: #8bc34a;
    }
  }

</style>