<script>
import { h } from "vue";

export default {
    name: "ButtonTimer",
    data() {
        return {
            seconds: 0,
        };
    },
    props: {
        countSeconds: {
            type: Number,
            require: true,
        },
    },
    methods: {
        decreaseTimer(seconds) {
            this.seconds = seconds;

            const timer = setInterval(() => {
                this.seconds -= 1;
                if (this.seconds === 0) {
                    clearInterval(timer);
                }
            }, 1000);
        },
    },
    computed: {
        prettyTime() {
            const minutes = Math.floor(this.seconds / 60);
            const seconds = this.seconds - minutes * 60;

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
        this.decreaseTimer(this.countSeconds);
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
