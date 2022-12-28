<script>
import { h } from "vue";
import ButtonTimer from "@/components/ButtonTimer.vue";

export default {
    props: {
        href: {
            type: String,
            required: false,
        },
        timer: {
            type: Number,
            required: false,
        },
        icon: {
            type: String,
            required: false,
        },
        theme: {
            type: String,
            required: false,
        },
        text: {
            type: String,
            required: false,
        },
    },
    methods: {
        generateBtn(href, theme, icon, timer, text) {
            const template = {
                type: "",
                props: {},
                children: [],
            };

            //устанавливает тип генерируемого блока и стандартный класс
            const setType = (href, theme) => {
                if (href) {
                    template.type = "a";
                    template.props.class = ["link"];
                    template.props.href = href;
                } else {
                    template.type = "button";
                    template.props.class = ["btn"];
                    checkTheme(theme);
                }
            };

            //проверяем наличие темы и устанавливаем класс при необходимости
            const checkTheme = (theme) => {
                if (!theme) {
                    template.props.class.push("btn_transparent");
                } else {
                    template.props.class.push("btn_" + theme);
                }
            };

            //проверяем наличие иконки и добавляем в шаблон при необходимости
            const checkIcon = (icon) => {
                if (icon) {
                    template.children.push(
                        h("img", {
                            src: `@/assets/icons/${icon}.svg`,
                            class: "btn__icon"
                        })
                    );
                }
            };

            //проверяем наличие таймера и добавляем в шаблон при необходимости
            const checkTimer = (timer) => {
                if (timer) {
                    template.children.push(
                        h(ButtonTimer, { countSeconds: timer })
                    );
                }
            };

            //проверяем наличие текста и добавляем в шаблон
            const checkText = (text) => {
                if (text) {
                    template.children.push(
                        h("span", { class: "btn__text" }, text)
                    );
                }
            };

            setType(href, theme);
            checkIcon(icon);
            checkText(text);
            checkTimer(timer);

            return template;
        },
    },

    render() {
        const template = this.generateBtn(
            this.href,
            this.theme,
            this.icon,
            this.timer,
            this.text
        );
        return h(template.type, template.props, template.children);
    },
};
</script>

<style lang="scss">
@font-face {
    font-family: "PhosphateSolid";
    src: url("@/assets/fonts/PhosphateSolid.ttf");
}

@font-face {
    font-family: "Nunito";
    src: url("@/assets/fonts/Nunito-Bold.ttf");
}

.link {
    color: #fff;
    font-family: "Nunito", sans-serif;
    font-size: 16px;
    font-weight: 700;
    line-height: 18px;
    text-decoration: underline;
    &:hover {
        color: #767679;
    }
    &:active {
        color: #c4296c;
    }
}

.btn {
    align-items: center;
    border: none;
    border-radius: 20px;
    color: #ffffff;
    cursor: pointer;
    display: flex;
    font: 400 18px/24px "PhosphateSolid";
    height: 60px;
    justify-content: center;
    padding-left: 15px;
    padding-right: 15px;

    @media (max-width: 640px) {
        height: 52px;
        padding-left: 14px;
        padding-right: 14px;
    }

    &_primary {
        background: #702c7e;
    }

    &_secondary {
        background: #c4296c;
    }

    &_warning {
        background: #f4ba46;
    }

    &_info {
        background: #0083b6;
    }

    &_danger {
        background: #df3f3e;
    }

    &_action {
        background: #ed732e;
    }

    &_transparent {
        background: transparent;
    }

    &_question {
        background: #6dd1b0;
    }

    &:disabled {
        background: #efefef;
        color: #767679;
    }

    &__icon {
        width: 30px;

        @media (max-width: 640px) {
            width: 24px;
        }
    }

    &__text {
        margin-left: 6px;
        margin-right: 6px;
    }
}
</style>
