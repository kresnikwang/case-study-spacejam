<template lang="pug">

  #app(style="background-image: url('static/bg.jpg')")

    .center-wrap

      section.header
        img.satellite(src="static/satellite.png")
        img.logo(src="static/lockup.png")
        h1 AN INTERGALATIC INTERACTIVE WECHAT TAKEOVER

      section.csv

        video(
          ref="videoCsv"
          v-show="video == 'csv'"
          src="static/videos/AKQA_JORDAN_SPACEJAM_DEFY_20022017_LO.mp4"
          autoplay
          controls
        )

        video(
          ref="videoUx"
          v-show="video == 'ux'"
          src="static/videos/JORDAN_SPACEJAM_UX_JOURNEY_20170119.mp4"
          controls
        )

        .toggle
          .item(v-on:click="playCSV()" v-bind:class="{'active': video == 'csv'}")
            h1 CASE FILM
          .bar |
          .item(v-on:click="playUX()" v-bind:class="{'active': video == 'ux'}")
            h1 UX JOURNEY

        .arrow(v-bind:class="{'hide': scroll > 0}")



      section.qr
        .wrap
          img(src="static/qr.png")
        .copy scan the code to defy the monstArs



      section.hero
        .content
          img(src="static/hero.png")
          video(
            ref="videoHeader"
            src="static/videos/ScreenRecordDefy.mp4"
            autoplay
            loop
            controls
            muted
          )

      section.idea
        ul
          li
            h2 THE CHALLENGE
            .para
              p On Space Jam’s 20th anniversary, the original super team  - The Monstars - are back and they’ve taken over the courts! The challenge was to get this nation’s ballers to defy them with the new AJ I and AJ XXXI Space Jam colorway before it’s too late.

          li
            h2 THE STRATEGY
            .para
              p With the Monstars taking over the interwebs, what’s the best way to get these ballers Fight back? Give a shoutout on WeChat - China’s most popular social network - and create an awesome takeover

          li
            h2 THE IDEA
            .para
              p Defy The Post : WeChat Takeover - A gamified mobile WeChat experience with the Monstars at the helm, filling up your social feed with. The takeover gets ballers to play for their social feed and take back control.

      section.ui

        h1 THE EXECUTION

        .para
          p Users who experience the takeover will get to play two different basketball modes with NBA superstar Jimmy Butler on this intergalactic basketball challenge.
          p These games will be in the form of two of China’s most influential sites Tencent NBA and Hypebeast.

        ul
          li
            .video
              img(src="static/phone-frame.png")
              video(
                ref="video1"
                src="static/videos/spin.mp4"
                autoplay
                loop
                muted
                controls
                v-on:mouseover="onMouseOver"
              )
            h2
              div HYPEBEAST
              div HURRICANE SPIN
            p Spin the ball to create a hurricane that blows away the Monstars at the Hypebeast site. The faster the spin, the crazier the site breaks, getting users through to the galaxy.
          li
            .video
              img(src="static/phone-frame.png")
              video(
                ref="video2"
                src="static/videos/wechat.mp4"
                autoplay
                loop
                muted
                controls
                v-on:mouseover="onMouseOver"
              )
            h2
              div WECHAT FEED
              div TAKEOVER
            p Baller's Moments Feed would be taken over by Faux Monstars posts to show their dominance. Influencers such as Li Na, Wang Da Lei, and Blackie Chen also drops in to make a cameo.
          li
            .video
              img(src="static/phone-frame.png")
              video(
                ref="video3"
                src="static/videos/satellite.mp4"
                autoplay
                loop
                muted
                controls
                v-on:mouseover="onMouseOver"
              )
            h2
              div TENCENT NBA
              div SATELLITE HOOPS
            p On the Tencent site, a moving satellite hoop will be hovering for users to score on. Shoot the ball to activate the satellite’s lasers. Make 3 shots in a row to obliterate it to smithereens.

        h3.blue
          div Complete the game to get to Jordan.com
          div and gear up by preordering the AJ I and AJ XXXI Space Jam colorway




      section.results
        h1 THE RESULTS

        ul
          li
            .num 144,000
            .label
              p BALLERS
              p DEFIED THE MONSTARS
          li
            .num 32,000
            .label
              p JOINED THE OFFICIAL
              p JORDAN WECHAT ACCOUNT
          li
            .num 456,000
            .label
              p WECHAT TAKEOVER
              p PARTICIPANTS


</template>

<script>

export default {
  name: 'app',
  mounted () {
    this.videos = [
      this.$refs.videoCsv,
      this.$refs.videoHeader,
      this.$refs.video1,
      this.$refs.video2,
      this.$refs.video3
    ]

    for (let video of this.videos) {
      video.addEventListener('volumechange', this.onVolumeChange)
    }

    window.addEventListener('scroll', this.onScroll)

  },
  data () {
    return {
      video: 'csv',
      scroll: 0
    }
  },
  methods: {
    onScroll (evt) {
      this.scroll = window.scrollY
    },
    onMouseOver (evt) {
      // this.$refs.video1.muted = true
      // this.$refs.video2.muted = true
      // this.$refs.video3.muted = true
      // evt.target.muted = false

    },
    onVolumeChange (evt) {

      if (evt.target.muted) return

      for (let video of this.videos) {
        if (video == evt.target) {
          continue
        }
        video.muted = true
      }
    },
    playCSV () {
      this.video = 'csv'
      this.$refs.videoUx.pause()
      this.$refs.videoCsv.play()
    },
    playUX () {
      this.video = 'ux'
      this.$refs.videoCsv.pause()
      this.$refs.videoUx.play()
    }
  }
}
</script>

<style lang="sass">

$cl-purple: #6D86E1

@font-face
  font-family: "Jordan"
  src: url("./assets/fonts/Jordan_Druk-Bold.otf") format("opentype")
  font-weight: bold

@font-face
  font-family: "Jordan"
  src: url("./assets/fonts/Jordan_NHG_Disp-55Roman.otf") format("opentype")
  font-weight: normal



html, body
  margin: 0
  padding: 0
  background-color: black
  font-family: "Jordan", Helvetica, Arial

body
  letter-spacing: 0.1em
  line-height: 1.4

ul, li
  list-style: none
  padding: 0

h1
  font-size: 28px
  line-height: 1.1
  letter-spacing: 0.2em
  margin: 0.2em auto

h2
  font-size: 24px
  letter-spacing: 0.2em
  margin: 0.2em auto
  line-height: 1.15

p
  font-size: 13px

#app
  // font-family: 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: white
  min-width: 900px
  position: relative
  background-size: 100% auto
  background-repeat: no-repeat
  background-position: center -80px
  padding: 30px 0px 0px

.center-wrap
  width: 900px
  margin: 0 auto

ul
  display: flex
  flex-direction: row

  li
    flex: 1
    padding: 0px 16px


h2
  color: $cl-purple

section.header

  .logo
    position: relative
    width: 240px
    display: block
    margin: 10px auto
    z-index: 2

  .satellite
    position: absolute
    left: 5%
    top: 3%
    width: 250px
    z-index: 1

  h1
    position: relative
    font-size: 24px
    letter-spacing: 5px
    text-shadow: 1px 1px 2px black
    z-index: 2

section.csv
  position: relative
  z-index: 3
  margin-top: 40px

  video
    border: 20px solid black
    width: 100%
    box-sizing: border-box

  .toggle
    font-weight: bold
    margin-top: 20px
    white-space: nowrap
    text-align: center

    h1
      font-size: 24px
      letter-spacing: 5px
      display: inline

    >*
      display: inline-block
      vertical-align: middle

    .bar
      margin: 0 20px
      font-size: 24px

    .item
      cursor: pointer
      width: 134px

      &.active h1
        color: $cl-purple
        pointer-events: none
        // border-bottom: 2px solid $cl-purple

  .arrow
    width: 60px
    height: 30px
    margin: 0 auto
    transition: all 0.6s ease 0s

    &:before, &:after
      content: ''
      display: block
      position: absolute
      bottom: 0
      left: 50%
      margin-left: -15px
      width: 30px
      height: 4px
      background: white

    &:before
      transform-origin: bottom right
      transform: rotate(-45deg)
      margin-left: -9px

    &:after
      transform-origin: bottom left
      transform: rotate(45deg)
      margin-left: -21px


    &.hide
      opacity: 0




section.qr
  margin: 90px auto 50px
  // padding-bottom: 100px

  .wrap
    display: inline-block
    background: black
    width: 200px

    img
      width: 100%

  .copy
    margin-top: 10px
    text-transform: uppercase
    font-size: 10px




section.hero
  // width: 60%
  width: 100%
  margin: 0% auto

  .content
    position: relative
    width: 800px
    margin: 0 auto

  img
    // max-width: 800px
    position: relative
    width: 100%
    margin-left: -32px

  video
    $size: 236px
    width: $size
    position: absolute
    z-index: 2
    top: 112px
    left: 50%
    margin-left: -$size / 2 + 0px

section.idea
  p
    margin: 0
    text-align: justify

section.ui

  .para
    p
      margin: 0.4em auto

  h1
    color: $cl-purple
    margin-top: 70px

  h3
    text-transform: uppercase
    font-size: 12px
    letter-spacing: 0.25em
    line-height: 1.7
    font-weight: normal
    margin-bottom: 30px

    &.blue
      font-size: 20px
      margin: 80px auto
      // color: $cl-purple
      font-weight: bold
      line-height: 1.3

  li
    width: 33.333333%

    .video
      position: relative

    img
      width: 250px

    video
      position: absolute
      top: 73px
      left: 48px
      width: 172px

    p
      margin: 0
      text-align: justify
    //   white-space: preline

section.results
  padding-bottom: 150px
  h1
    color: $cl-purple
    // margin-top: 100px

  .num
    color: $cl-purple
    font-size: 46px
    font-weight: bold
    letter-spacing: 0.15em
    margin-bottom: -0.15em

  p
    margin: 0 auto



.fade-enter-active
  transition: all 0.8s ease 0s

.fade-enter
  opacity: 0

.fade-leave-active
  transition: all 0.4s ease 0s
  opacity: 0


</style>
