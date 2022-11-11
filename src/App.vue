<template>
  <q-layout view="lHh Lpr lFf" class="shadow-2 rounded-borders">
    <q-header
      reveal
      class="bg-pink-1 text-pink-10"
      :class="leftDrawerOpen ? 'q-ml-sm round' : ''"
    >
      <q-toolbar>
        <q-btn
          flat
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />

        <q-toolbar-title> Mindhive </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      style="gap: 150px"
      class="bg-blue-2 shadow-3 gap-2 round"
    >
      <q-list>
        <q-item-label
          header
          class="text-blue-8 q-ml-sm"
          style="font-size: 2em; font-weight: 700"
          >About me</q-item-label
        >
        <q-item
          v-for="item in sidebar"
          :key="item.name"
          clickable
          tag="a"
          class="q-my-md q-mx-md round"
          :class="item.bg"
          target="_blank"
          :href="item.link"
        >
          <q-item-section avatar>
            <q-icon class="rounded" :class="item.bg2" :name="item.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label :class="item.bg">{{ item.name }}</q-item-label>
            <q-item-label :class="item.bg" caption>{{ item.sub }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <div class="row q-pa-lg" style="height: 150px">
        <div class="col-sm-6 relative">
          <q-icon
            name="arrow_back"
            size="20px"
            class="absolute"
            style="top: 80px"
          />
          <div class="flex items-center q-mb-lg q-ml-xl relative">
            <q-avatar
              color="grey-9"
              text-color="white"
              size="30px"
              class="q-mr-sm"
              >W</q-avatar
            >
            <span style="font-weight: 700">Wardah</span>
          </div>
          <div class="q-ml-xl q-mt-lg">
            <p class="text-grey-7 text-weight-bold">
              Pure set
              <br />
              <span class="text-h4 text-weight-bold text-black">$65.00 </span>
            </p>
            <div class="q-mt-xl">
              <q-img
                src="https://images.tokopedia.net/img/cache/900/VqbcmM/2020/8/23/3295c2a9-08b1-46ca-96e7-ff10ca4a7090.jpg"
                style="max-width: 60%; height: auto; border-radius: 10px"
                alt="product picture"
              />
            </div>
          </div>
        </div>
        <div class="col-sm-6 q-px-lg">
          <q-card
            style="
              height: 100%;
              min-height: 40vw;
              border-radius: 20px;
              text-align: center;
              align-items: center;
              width: 100%;
            "
            class="q-pa-xl"
          >
            <q-btn
              @click="confirm = true"
              no-caps
              style="width: 100%; border-radius: 10px"
              class="flex items-center bg-black text-white q-mx-auto q-pa-sm"
            >
              <q-img
                src="https://www.freepnglogos.com/uploads/apple-logo-png/apple-logo-png-dallas-shootings-don-add-are-speech-zones-used-4.png"
                style="width: 16px"
                class="white q-mr-sm"
              />Pay
            </q-btn>
            <div class="text-divider q-mt-md flex justify-center text-grey-5">
              Or pay with card
            </div>
            <div class="text-left q-mt-md">
              Shipping Information
              <q-input
                outlined
                v-model="text"
                label="Email"
                stack-label
                color="blue-5"
              />
              <br />
              <q-select
                outlined
                v-model="model"
                :options="['USA', 'Indonesia', 'Australia', 'Korea']"
                label="Shipping Address"
              />

              <q-input
                outlined
                v-model="text"
                label="Name"
                stack-label
                color="blue-5"
              />

              <q-input
                outlined
                v-model="text"
                label="Address"
                stack-label
                color="blue-5"
              />
              <a class="text-black" style="font-size: 12px" href="#"
                >Enter address manually</a
              >
              <br />
              <br />
              Payment Details
              <q-input v-model="text">
                <template v-slot:append>
                  <div v-for="item in imagesCard" :key="item.link">
                    <img style="height: 20px" :src="item.link" />
                  </div>
                </template>
              </q-input>
              <div class="row">
                <div class="col">
                  <q-input
                    style="font-size: 10px"
                    outlined
                    v-model="text"
                    label="MM/YY"
                  />
                </div>
                <div class="col">
                  <q-input outlined v-model="text" label="CVC" />
                </div>
              </div>
            </div>
            <q-checkbox
              style="float: left"
              v-model="right"
              label="Billing address is same as shipping"
            />
            <q-btn
              @click="confirm = true"
              no-caps
              style="width: 100%; border-radius: 10px"
              class="flex items-center bg-black text-white q-mx-auto q-pa-sm"
            >
              Pay $65.00
            </q-btn>
          </q-card>
        </div>
      </div>
    </q-page-container>
    <q-dialog v-model="confirm" persistent>
      <q-card style="width: 500px">
        <q-card-section class="row items-center bg-blue-1 round">
          <q-avatar icon="school" color="blue-2" text-color="blue-10" />
          <span class="q-ml-sm text-weight-bold text-blue-10"
            >So, Do you wanna hire me?</span
          >
        </q-card-section>

        <q-card-actions align="right" class="bg-blue-1">
          <q-btn
            label="Wait"
            color="pink-1"
            text-color="pink-10"
            v-close-popup
          />

          <a
            class="text-green-10"
            href="https://api.whatsapp.com/send/?phone=628973180644&text&type=phone_number&app_absent=1"
            target="_blank"
          >
            <q-btn
              color="teal-1"
              text-color="green-10"
              @click="window.location.href('wa.me/628973180644')"
            >
              Yes
            </q-btn>
          </a>
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  name: "OnePage",

  components: {
    // HelloWorld,
  },

  data() {
    return {
      title: "App Test Kabloom",
      sidebar: [
        {
          name: "Curiculum Vitae",
          sub: "Front End Developer",
          icon: "school",
          bg2: "bg-green-2",
          bg: "bg-green-1 text-green-9",
          link: "https://drive.google.com/file/d/1WwrZq7nV-gBQDXbkbkBKhwoEfCeY3i7z/view?usp=share_link",
        },
        {
          name: "Github",
          sub: "Just my repo",
          icon: "code",
          bg2: "bg-pink-2",
          bg: "bg-pink-1 text-pink-9",
          link: "https://github.com/Arsfbrynt",
        },

        {
          name: "Email",
          sub: "Contact me",
          icon: "email",
          bg2: "bg-blue-2",
          bg: "bg-blue-1 text-blue-9",
          link: "mailto:arsfbrynt@gmail.com",
        },
      ],
      model: "",
      right: true,
      confirm: false,

      imagesCard: [
        {
          link: "https://image.cermati.com/q_70/v1431504749/ogxuwgtitfwxavibahws.webp",
        },
        {
          link: "https://image.cermati.com/q_70,w_1200,h_800,c_fit/v1431504770/xnibjctvybqrvqycwd1v.png",
        },
        {
          link: "https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/American_Express_logo_%282018%29.svg/1200px-American_Express_logo_%282018%29.svg.png",
        },
        {
          link: "https://upload.wikimedia.org/wikipedia/commons/a/a6/Diners_Club_Logo3.svg",
        },
      ],
    };
  },
  methods: {
    goLink() {
      const link = "google.com";
      window.location.href(link);
    },
  },

  setup() {
    return { leftDrawerOpen: ref(false) };

    // return {
    //   leftDrawerOpen: ref(false),
    // };
  },
};
</script>
<style>
.q-focus-helper {
  opacity: 0 !important;
}
.round {
  border-radius: 10px;
}
.rounded {
  border-radius: 50%;
  padding: 6px;
  box-shadow: 0px 0.5px 2px #888888;
}
.white {
  filter: invert(100%);
}
.text-divider {
  --text-divider-gap: 1rem;
  display: flex;
  align-items: center;
}
.text-divider::before,
.text-divider::after {
  content: "";
  height: 1px;
  background-color: silver;
  flex-grow: 1;
}
.text-divider::before {
  margin-right: var(--text-divider-gap);
}
.text-divider::after {
  margin-left: var(--text-divider-gap);
}
a {
  text-decoration: unset !important;
}
</style>
