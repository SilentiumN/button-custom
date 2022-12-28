<script>
import { h } from "vue";

export default {
    name: "ButtonTimer",
    data() {
        return {
            milliseconds: 0,
        };
    },
    props: {
        countMilliseconds: {
            type: Number,
            require: true,
        },
    },
    methods: {
        decreaseTimer(milliseconds) {
            this.milliseconds = milliseconds;

            const timer = setInterval(() => {
                if (this.milliseconds >= 1000) {
                    this.milliseconds -= 1000;
                }
                else {
                    clearInterval(timer);
                }
            }, 1000);
        },
    },
    computed: {
        prettyTime() {
            const minutes = Math.floor(this.milliseconds / 1000 / 60);
            const seconds = Math.floor(this.milliseconds / 1000) - minutes * 60;

            const doPrettyTime = (number) => {
                if (number < 10) {
                    return "0" + number;
                } else {
                    return number;
                }
            };

            return doPrettyTime(minutes) + ":" + doPrettyTime(seconds);
        },
    },
    mounted() {
        this.decreaseTimer(this.countMilliseconds);
    },
    render() {
        return h("div", { class: "timer" }, [this.prettyTime]);
    },
};
</script>

<style lang="scss">
.timer {
    background: #d52830;
    border-radius: 15px;
    color: #ffffff;
    padding-top: 1px;
    padding-bottom: 1px;
    width: 54px;
}
</style>
