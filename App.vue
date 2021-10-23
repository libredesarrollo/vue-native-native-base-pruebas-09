	  <template>
  <nb-container v-if="isAppReady">
    <!-- header -->
    <nb-header>
      <nb-left>
        <nb-button
          transparent
          :on-press="
            () => {
              console.log('Hola Mundo');
            }
          "
        >
          <nb-icon name="arrow-back" />
        </nb-button>
      </nb-left>

      <nb-body>
        <nb-title>Experimentos</nb-title>
        <nb-subtitle>listado de pruebas con NB</nb-subtitle>
      </nb-body>

      <nb-right>
        <nb-button transparent>
          <nb-icon name="menu" />
        </nb-button>
      </nb-right>
    </nb-header>
    <!-- end header -->
    <!-- contenido -->

    <scroll-view>
      <nb-content>
        <!-- fab -->

        <nb-fab
          :on-press="
            () => {
              console.log('click');
            }
          "
          position="bottomLeft"
          :style="{ backgroundColor: 'red' }"
        >
          <nb-icon-nb name="md-share"></nb-icon-nb>
        </nb-fab>

        <nb-fab
          :active="false"
          direction="up"
          position="bottomRight"
          :style="{ backgroundColor: 'green' }"
        >
          <nb-icon-nb name="close"></nb-icon-nb>

          <nb-button :style="{ elevation: 500, backgroundColor: 'green' }">
            <nb-icon-nb name="logo-twitter"></nb-icon-nb>
          </nb-button>
          <nb-button :style="{ elevation: 500, backgroundColor: 'blue' }">
            <nb-icon-nb name="logo-facebook"></nb-icon-nb>
          </nb-button>
          <nb-button
            :on-press="
              () => {
                console.log('google');
              }
            "
            :style="{
              elevation: 500,

              backgroundColor: 'red',
            }"
          >
            <nb-icon-nb name="logo-google"></nb-icon-nb>
          </nb-button>
        </nb-fab>

        <!-- end fab -->

        <!-- form -->
        <nb-form>
          <nb-item>
            <nb-input placeholder="Nombre" />
          </nb-item>
          <nb-item>
            <nb-label>Apellido</nb-label>
            <nb-input />
          </nb-item>
          <nb-item floatingLabel>
            <nb-label>Edad</nb-label>
            <nb-input />
          </nb-item>
          <nb-item rounded>
            <nb-label>Profesion</nb-label>
            <nb-input />
          </nb-item>
          <nb-item success>
            <nb-label>Esta correcto</nb-label>
            <nb-input />
            <nb-icon name="checkmark-circle"></nb-icon>
          </nb-item>
          <nb-item error>
            <nb-label>Es incorrecto</nb-label>
            <nb-input />
            <nb-icon name="close-circle"></nb-icon>
          </nb-item>
          <nb-item last>
            <nb-label>Mas info</nb-label>
            <nb-input />
          </nb-item>
        </nb-form>

        <!-- end form -->
        <!-- cartas -->
        <nb-card>
          <nb-card-item header bordered>
            <nb-text> Titulo </nb-text>
          </nb-card-item>
          <nb-card-item footer bordered>
            <nb-body>
              <nb-text> Carta </nb-text>
            </nb-body>
          </nb-card-item>
          <nb-card-item footer bordered>
            <nb-text> Titulo </nb-text>
          </nb-card-item>
        </nb-card>
        <!-- end cartas -->

        <!-- botones -->
        <nb-button iconLeft>
          <nb-icon name="logo-google" />
          <nb-text>Boton</nb-text>
        </nb-button>

        <!-- grid -->
        <nb-grid>
          <nb-col :style="{ backgroundColor: 'red', width: 50 }">
            <nb-text> 1.1 </nb-text>
          </nb-col>
          <nb-col :style="{ backgroundColor: 'green' }">
            <nb-row :style="{ backgroundColor: 'black' }">
              <nb-text> 2.1 </nb-text>
            </nb-row>
            <nb-row :style="{ backgroundColor: 'yellow' }">
              <nb-text> 2.2 </nb-text>
            </nb-row>
          </nb-col>
          <nb-col :style="{ backgroundColor: 'blue', width: 100, height: 200 }">
            <nb-list>
              <nb-list-item>
                <nb-text> Item 1 </nb-text>
              </nb-list-item>
              <nb-list-item :selected="true">
                <nb-text> Item 2 </nb-text>
              </nb-list-item>
              <nb-list-item>
                <nb-text> Item 3 </nb-text>
              </nb-list-item>
            </nb-list>
          </nb-col>
        </nb-grid>
        <!-- endgrid -->
      </nb-content>
    </scroll-view>
    <!-- botones -->
    <!-- end contenido -->
    <nb-footer>
      <nb-footer-tab>
        <nb-button>
          <nb-text>Apps</nb-text>
        </nb-button>
        <nb-button>
          <nb-text>Camera</nb-text>
        </nb-button>
        <nb-button :active="true">
          <nb-text>Navigate</nb-text>
        </nb-button>
        <nb-button>
          <nb-text>Contact</nb-text>
        </nb-button>
      </nb-footer-tab>
    </nb-footer>
  </nb-container>
</template>

<script>
import Vue from "vue-native-core";
import { VueNativeBase } from "native-base";
import * as Font from "expo-font";
import { Ionicons } from "@expo/vector-icons";

import { Button, Container } from "native-base";

Vue.use(VueNativeBase);

export default {
  components: {
    Button,
    Ionicons,
    Font,
  },
  data() {
    return {
      isAppReady: false,
      form: {
        name: "Andres",
      },
    };
  },
  created() {
    this.loadFonds();
  },
  methods: {
    async loadFonds() {
      this.isAppReady = false;

      try {
        await Font.loadAsync({
          Roboto: require("./node_modules/native-base/Fonts/Roboto.ttf"),
          Roboto_medium: require("./node_modules/native-base/Fonts/Roboto_medium.ttf"),
          ionicons: Ionicons.font["ionicons"],
        });
        this.isAppReady = true;
      } catch (error) {
        console.log("Error al cargar la fuente ", error);
        this.isAppReady = true;
      }
    },
  },
};
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
</style>
