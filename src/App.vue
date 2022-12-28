<script>
import { h } from "vue";
import ButtonCustom from "@/components/ButtonCustom.vue";

export default {
    render() {
        return h("div", [
            h("div", [
              h(ButtonCustom, { href: "#", text: "Напомнить PIN" })
            ]),
            h("div", [
                h(ButtonCustom, { icon: "arrow", theme: "primary" }),
                h(ButtonCustom, { icon: "exit", theme: "danger" }),
                h(ButtonCustom, { icon: "quest", theme: "question" }),
                h(ButtonCustom, { icon: "chevron", theme: "primary" }),
                h(ButtonCustom, { icon: "google", theme: "danger" }),
                h(ButtonCustom, { icon: "vk", theme: "info" }),
                h(ButtonCustom, { icon: "class", theme: "action" }),
                h(ButtonCustom, { icon: "pen", theme: "primary" }),
            ]),
            h("div", [
                h(ButtonCustom, { timer: 10000, text: " Повторное письмо", theme: "info"}),
            ]),
            h("div", [
                h(ButtonCustom, { theme: "primary", text: "Отправить письмо" }),
                h(ButtonCustom, { theme: "secondary",  text: "Отправить письмо" }),
                h(ButtonCustom, { theme: "warning", text: "Отправить письмо" }),
                h(ButtonCustom, { text: "Отправить письмо", disabled: true }),
                h(ButtonCustom, { theme: "info", text: "Отправить письмо" }),
                h(ButtonCustom, { theme: "danger", text: "Отправить письмо" }),
                h(ButtonCustom, { theme: "action", text: "Отправить письмо" }),
                h(ButtonCustom, { theme: "info", text: "Отправить письмо", timer: 5000, icon: "chevron" }),
            ]),
        ]);
    },
};
</script>

<style lang="scss">
body {
    background: #1e1e1e;
}
</style>
