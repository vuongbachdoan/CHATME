<template>
    <v-app>
        <v-system-bar>
            <v-icon icon="mdi-wifi-strength-4"></v-icon>
            <v-icon icon="mdi-signal" class="ms-2"></v-icon>
            <v-icon icon="mdi-battery" class="ms-2"></v-icon>

            <span class="ms-2">3:13PM</span>
        </v-system-bar>
        <v-layout style="marginTop: 24px">
            <v-navigation-drawer v-model="drawer" :rail="rail" permanent @click="rail = false">
                <v-list-item prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg" title="John Leider" nav>
                    <template v-slot:append>
                        <v-btn variant="text" icon="mdi-chevron-left" @click.stop="rail = !rail"></v-btn>
                    </template>
                </v-list-item>

                <v-divider></v-divider>

                <v-list density="compact" nav>
                    <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
                    <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
                    <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
                </v-list>
            </v-navigation-drawer>

            <v-navigation-drawer floating permanent>
                <v-list density="compact" nav>
                    <v-list-item prepend-icon="mdi-view-dashboard" title="Home" value="home"></v-list-item>
                    <v-list-item prepend-icon="mdi-forum" title="About" value="about"></v-list-item>
                </v-list>
            </v-navigation-drawer>

            <v-main>
                <v-card class="mx-auto" color="grey-lighten-3" elevation="0">
                    <v-layout>
                        <v-app-bar>
                            <template v-slot:prepend>
                                <v-app-bar-nav-icon><v-icon>mdi-account-circle</v-icon></v-app-bar-nav-icon>
                            </template>

                            <v-app-bar-title>Elex John</v-app-bar-title>

                            <v-spacer></v-spacer>

                            <v-btn icon>
                                <v-icon>mdi-phone</v-icon>
                            </v-btn>

                            <v-btn icon>
                                <v-icon>mdi-video</v-icon>
                            </v-btn>

                            <v-btn icon>
                                <v-icon>mdi-information-outline</v-icon>
                            </v-btn>
                        </v-app-bar>

                        <v-main class="">
                            <v-container class=" pa-0 ">
                                <v-row class="no-gutters elevation-0">
                                    <v-col cols="auto" class="flex-grow-1 flex-shrink-0">
                                        <v-responsive v-if="activeChat" class="overflow-y-hidden ">
                                            <v-card flat class="d-flex flex-column  ">
                                                <v-card-text class="flex-grow-1 overflow-y-auto">
                                                    <template v-for="(msg, i) in messages">
                                                        <div :class="{ 'd-flex flex-row-reverse': msg.me }">
                                                            <v-menu offset-y>
                                                                <template v-slot:activator="{ on }">
                                                                    <v-hover v-slot:default="{ hover }">
                                                                        <v-chip :color="msg.me ? 'primary' : ''" dark
                                                                            style="height:auto;white-space: normal;"
                                                                            class="pa-4 mb-2" v-on="on">
                                                                            {{ msg.content }}
                                                                            <sub class="ml-2" style="font-size: 0.5rem;">{{
                                                                                msg.created_at }}</sub>
                                                                            <v-icon v-if="hover" small>
                                                                                mdi-chevron-down
                                                                            </v-icon>
                                                                        </v-chip>
                                                                    </v-hover>
                                                                </template>
                                                                <v-list>
                                                                    <v-list-item>
                                                                        <v-list-item-title>delete</v-list-item-title>
                                                                    </v-list-item>
                                                                </v-list>
                                                            </v-menu>
                                                        </div>
                                                    </template>
                                                </v-card-text>
                                                <v-card-text class="flex-shrink-1">
                                                    <v-text-field label="" prepend-inner-icon="mdi-emoticon"
                                                        append-icon="mdi-send" variant="outlined">
                                                    </v-text-field>
                                                </v-card-text>
                                            </v-card>
                                        </v-responsive>
                                    </v-col>
                                </v-row>
                            </v-container>
                        </v-main>
                    </v-layout>
                </v-card>
            </v-main>
        </v-layout>
    </v-app>
</template>

<script>
export default {
    data() {
        return {
            activeChat: 1,
            messages: [
                {
                    content: "lorem ipsum",
                    me: true,
                    created_at: "11:11am"
                },
                {
                    content: "dolor",
                    me: false,
                    created_at: "11:11am"
                },
                {
                    content: "dolor",
                    me: false,
                    created_at: "11:11am"
                },
                {
                    content: "dolor",
                    me: false,
                    created_at: "11:11am"
                },
                {
                    content: "dolor",
                    me: true,
                    created_at: "11:11am"
                },
                {
                    content: "dolor",
                    me: false,
                    created_at: "11:12am"
                },
                {
                    content: "dolor",
                    me: false,
                    created_at: "11:14am"
                }
            ],
            messageForm: {
                content: "",
                me: true,
                created_at: "11:11am"
            },
            drawer: true,
            rail: true,
        }
    },
}
</script>

<style></style>