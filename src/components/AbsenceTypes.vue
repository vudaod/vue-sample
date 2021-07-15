  <template>
  <div class="center grid">
    <vs-row>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="1">
        Show
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="11">
        <vs-select
          filter
          multiple
          placeholder="Absence Types"
          v-model="selected"
        >
          <vs-option
            v-for="(item, index) in AbsenceTypes"
            :key="index"
            :value="item.name"
            >{{ item.name }}
          </vs-option>
        </vs-select>
      </vs-col>
    </vs-row>
  </div>
</template>
<script lang="ts">
import { Component, Emit, Vue, Watch } from "vue-property-decorator";

@Component
export default class AbsenceTypes extends Vue {
  private selected: string = "";
  private AbsenceTypes = [
    { id: 1, name: "Paid Vacations" },
    { id: 2, name: "Illness" },
    { id: 3, name: "Home Office" },
    { id: 4, name: "Absence" },
  ];
  @Watch("selected")
  @Emit("SelectAbsenceTypes")
  SelectAbsenceTypes() {
    return this.selected;
  }
}
</script>