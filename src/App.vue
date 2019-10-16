<template>
  <div class="container">
    <div class="accordion">
      <div class="card" :class="{show: isExpanded, multilevel: isExpanded2}">
        <div class="header" :class="{multilevel: isExpanded2}" @click="toggleState()">
          <i class="material-icons">home</i>
          <h2>Início</h2>
          <i class="icon material-icons">keyboard_arrow_down</i>
        </div>
        <div class="content" :class="{show: isExpanded}">
          <div class="content-header" :class="{multilevel: isExpanded2}">
            <h4>Geral</h4>
          </div>
          <div class="content-body" :class="{multilevel}">
            <div class="card" :class="{show: isExpanded2}">
              <div class="header" @click="toggleState2()">
                <i class="material-icons">alarm</i>
                <h2>Alarmes</h2>
                <i class="icon material-icons">keyboard_arrow_down</i>
              </div>
              <div class="content" :class="{show: isExpanded2}">
                <div class="content-header">
                  <h4>Geral</h4>
                </div>
                <div class="content-body">
                  Teste
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="card" :class="{show: false}">
        <div class="header">
          <i class="material-icons">person</i>
          <h2>Perfil</h2>
          <i class="icon material-icons">keyboard_arrow_down</i>
        </div>
        <div class="content" :class="{show: false}">
          <div class="content-header">
            <h4>Content title</h4>
          </div>
          <div class="content-body">
            Teste
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: () => ({
    multilevel: true,
    isExpanded: false,
    isExpanded2: false,
    group: [
      {
        icon: 'home',
        title: 'Início',
        content: 'Conteúdo'
      },
      {
        icon: 'person',
        title: 'Perfil',
        content: 'Conteúdo'
      }
    ]
  }),
  methods: {
    toggleState() {
      this.isExpanded = !this.isExpanded;
      if(!this.isExpanded) {
        this.isExpanded2 = false;
      }
    },
    toggleState2() {
      this.isExpanded2 = !this.isExpanded2;
    }
  }
}
</script>

<style lang="scss">
@import '~material-design-icons/iconfont/material-icons.css';
body {
  background: #eee;
  font-family: sans-serif;
}
.container {
  margin: 0 auto;
  max-width: 500px;
  width: 100%;
}
.accordion {
  width: 100%;
  
  .card {
    width: 100%;
    overflow: hidden;
    border: 1px solid #ccc;
    border-bottom: none;
    transition: all 300ms;

    &:first-of-type {
      border-radius: 4px 4px 0 0;
    }
    &:last-of-type {
      border-radius: 0 0 4px 4px;
      border: 1px solid #ccc;
    }
    &:only-of-type {
      border-radius: 4px;
      border: 1px solid #ccc;
    }

    &.show {
      margin: 15px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-shadow: 0px 1px 2px #aaa;

      & > .header > .icon {
        transform: rotateZ(180deg);
      }
    }
    &.show.multilevel {
      border: 1px solid transparent;
      box-shadow: none;
      margin: 15px 0 0;
    }

    .header {
      background: white;
      display: flex;
      align-items: center;
      padding: 15px;
      position: relative;

      &:hover {
        background: rgba(0,0,0,0.1);
      }
      &.multilevel {
        border: 1px solid #ccc;
        border-bottom: none;
        border-radius: 4px 4px 0 0;
      }

      h2 {
        margin: 0;
        padding: 0;
        margin-left: 15px;
      }
      .icon {
        position: absolute;
        right: 15px;
        cursor: pointer
      }
    }
  }
  .content {
    display: none;

    &.show {
      display: block;
    }

    .content-header {
      background: white;
      padding: 15px;

      &.multilevel {
        border: 1px solid #ccc;
        border-top: none;
        border-radius: 0 0 4px 4px;
      }
      
      h4 {
        margin: 0;
        padding: 0;
        color: #888;
      }
    }
    .content-body {
      background: white;
      padding: 15px;

      &.multilevel {
        background: transparent;
        padding: 0px;
      }
      .card {
        border: none;
      }
      .card.show {
        border: 1px solid #ccc;
      }
    }
  }
}
</style>
