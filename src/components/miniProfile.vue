<template>
  <v-card class="px-2">
    <v-card-title>
      <v-avatar size="120">
        <img
          alt="user"
          :src="
            person.avtUrl ||
              'data:image/png;base64,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'
          "
        />
      </v-avatar>
      <p class="ml-6 font-weight-bold text-h4 my-auto">
        {{person.name||"Name"}}
        <v-btn
          color="green"
          dark
          elevation="2"
          fab
          x-small
          rounded
          @click="dialog = true"
        >
          <v-icon>mdi-pencil</v-icon>
        </v-btn>
        <v-dialog max-width="600px" v-model="dialog">
          <v-card>
            <v-app-bar dark color="primary">
              <h2>Cập nhật thông tin cá nhân</h2>
            </v-app-bar>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12">
                    <v-text-field
                      v-model="name"
                      label="Họ Và Tên"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      v-model="email"
                      label="Email"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <div>
                      <v-menu
                        ref="menu"
                        v-model="menu"
                        :close-on-content-click="false"
                        transition="scale-transition"
                        offset-y
                        min-width="auto"
                      >
                        <template v-slot:activator="{ on, attrs }">
                          <v-text-field
                            v-model="date"
                            label="Birthday date"
                            prepend-icon="mdi-calendar"
                            readonly
                            v-bind="attrs"
                            v-on="on"
                          ></v-text-field>
                        </template>
                        <v-date-picker
                          v-model="date"
                          :active-picker.sync="activePicker"
                          :max="
                            new Date(
                              Date.now() -
                                new Date().getTimezoneOffset() * 60000
                            )
                              .toISOString()
                              .substr(0, 10)
                          "
                          min="1950-01-01"
                          @change="save"
                        ></v-date-picker>
                      </v-menu>
                    </div>
                  </v-col>
                  <v-col>
                    <v-text-field
                      name="avt"
                      label="Avatar URL"
                      v-model="avtUrl"
                    ></v-text-field>
                  </v-col>
                  <v-col>
                    <v-avatar size="80" color="warning">
                      <img :src="avtUrl" />
                    </v-avatar>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="personUpdate(name, date, email, avtUrl);dialog = false;">
                Cập Nhật
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </p>
    </v-card-title>
    <v-divider></v-divider>
    <v-card-text>
      <div class="font-weight-bold ml-8 mb-2 text-align-center">
        Birthday: {{ person.dateOfBirth }} <br />
        Email: {{ person.email }} <br />
        {{ person.personAddress }}
      </div>

      <v-dialog transition="dialog-bottom-transition" max-width="1000">
        <template v-slot:activator="{ on, attrs }">
          <v-btn class="ml-8 mt-3" color="primary" v-bind="attrs" v-on="on"
            >My Certificate</v-btn
          >
        </template>
        <template v-slot:default>
          <v-card>
            <v-card-title>
              Danh Sách Chứng Nhận Của Tôi
              <v-spacer></v-spacer>
              <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
            :headers="headers"
            :items="person.cers"
            :search="search"
            height="450"
          >
            <template v-slot:item.date="{ item }">
              {{ time(item.date) }}
            </template>
            <template v-slot:item.action="{ item }">
              <v-dialog transition="dialog-bottom-transition" max-width="600">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn color="primary" icon v-bind="attrs" v-on="on">
                    <v-icon>mdi-information</v-icon>
                  </v-btn>
                </template>
                <template v-slot:default>
                  <v-card>
                    <v-toolbar color="primary" dark
                      ><h2>Thông tin chi tiết</h2></v-toolbar
                    >
                    <v-card-text class="mt-3">
                      <v-container fluid>
                        <v-row>
                          <v-col cols="12"
                            ><h1 align="center">{{ item.name }}</h1>
                          </v-col>
                          <v-col cols="12"
                            ><h3 class="px-8" align="center">
                              {{ item.content }}
                            </h3>
                          </v-col>
                          <v-col cols="6">
                            <h3>From: {{ item.author }}</h3>
                            <h3>
                              To: <span class="address">{{ item.person }}</span>
                            </h3>
                          </v-col>
                          <v-divider vertical></v-divider>
                          <v-col cols="6" align="center">
                            <h4 align="center">{{ time(item.date) }}</h4>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col cols="6" align="center">
                            <h4 align="center" class="mt-2">Mã Băm Nội Dung</h4>
                            <span align="center">
                              <img :src="'http://api.qrserver.com/v1/create-qr-code/?data='+contentHash(item.name, item.content, item.person)+'&size=150x150'"/>
                            </span>
                          </v-col>
                          <v-divider vertical></v-divider>
                          <v-col cols="6" align="center">
                            <h3 class="mt-2">Chữ Ký</h3>
                            <img :src="'http://api.qrserver.com/v1/create-qr-code/?data='+item.signature+'&size=150x150'"/>
                          </v-col>
                        </v-row>
                      </v-container>
                    </v-card-text>
                  </v-card>
                </template>
              </v-dialog>
            </template>
          </v-data-table>
          </v-card>
        </template>
      </v-dialog>
    </v-card-text>
  </v-card>
</template>

<script>
import {web3, contract } from "../web3/web3";
export default {
  data() {
    return {
      dialog: null,
      person: {},
      activePicker: null,
      date: null,
      menu: false,
      avtUrl: "",
      search: "",
      headers: [
        { text: "Chứng Nhận", value: "name" },
        { text: "Người Nhận", value: "person" },
        { text: "Thời Điểm Cấp", value: "date" },
        { text: "Chi Tiết", value: "action" },
      ],
      name:'',
      email:'',

    };
  },
  watch: {
    menu(val) {
      val && setTimeout(() => (this.activePicker = "YEAR"));
    },
  },
  methods: {
    contentHash(name, content, person) {
      return web3.utils.sha3(name + content + person);
    },
    time(stamp) {
      var m = new Date(stamp * 1000);
      return (
        m.getUTCFullYear() +
        "/" +
        (m.getUTCMonth() + 1) +
        "/" +
        m.getUTCDate() +
        " " +
        m.getUTCHours() +
        ":" +
        m.getUTCMinutes() +
        ":" +
        m.getUTCSeconds()
      );
    },
    personUpdate(name, date, email, avt) {
      contract.methods
        .personUpdate(name, date, email, avt)
        .send({ from: this.$store.state.address })
        .on("receipt", () => {
          contract.methods
            .getPerson()
            .call({ from: this.$store.state.address })
            .then((data) => {
              this.person = data;
              console.log(
                this.person.personAddress ==
                  "0x0000000000000000000000000000000000000000"
              );
              if (
                this.person.personAddress ==
                "0x0000000000000000000000000000000000000000"
              ) {
                console.log(this);
                this.dialog = true;
              }
            });
        });
    },
    save(date) {
      this.$refs.menu.save(date);
    },
  },
  created() {
    console.log(this.$store.state.address);
    window.ethereum
      .request({
        method: "eth_requestAccounts",
      })
      .then((data) => {
        this.$store.state.address = data[0];
        contract.methods
          .getPerson()
          .call({ from: this.$store.state.address })
          .then((data) => {
            this.person = data;
            console.log(
              this.person.personAddress ==
                "0x0000000000000000000000000000000000000000"
            );
            if (
              this.person.personAddress ==
              "0x0000000000000000000000000000000000000000"
            ) {
              console.log(this);
              this.dialog = true;
            }
          });
      });
  },
};
</script>

<style scoped>
.address {
  font-size: 9px;
  font-weight: 300;
}</style>
