 <template>
  <div class="center grid">
    <vs-row>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="1">
        Filters
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="3">
        <div style="padding-right: 5px">
          <vs-select placeholder="Location" v-model="LocationSelected">
            <vs-option
              :label="item.name"
              v-for="(item, index) in Locations"
              :key="index"
              :value="item.name"
              >{{ item.name }}
            </vs-option>
          </vs-select>
        </div>
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="3">
        <div style="padding-right: 5px">
          <vs-select placeholder="Department" v-model="DepartmentSelected">
            <vs-option
              :label="item.name"
              v-for="(item, index) in Departments"
              :key="index"
              :value="item.name"
              >{{ item.name }}
            </vs-option>
          </vs-select>
        </div>
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="3">
        <vs-select placeholder="Team" v-model="TeamSelected">
          <vs-option
            :label="item.name"
            v-for="(item, index) in Teams"
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
export default class Filters extends Vue {
  private LocationSelected: string = "";
  private DepartmentSelected: string = "";
  private TeamSelected: string = "";
  private Locations = [
    { id: 1, name: "Munich" },
    { id: 2, name: "Berlin" },
    { id: 3, name: "HCMC" },
  ];
  private Departments = [
    { id: 1, name: "Customer Service" },
    { id: 2, name: "IT" },
  ];
  private Teams = [
    { id: 1, name: "Sales North" },
    { id: 2, name: "Sales South" },
    { id: 3, name: "Xamarin Team" },
    { id: 4, name: " Galeria Kaufhof" },
  ];
  @Watch("LocationSelected")
  @Emit("SelectLocation")
  SelectLocation() {
    return this.LocationSelected;
  }
  @Watch("DepartmentSelected")
  @Emit("SelectDepartment")
  SelectDepartment() {
    return this.DepartmentSelected;
  }
  @Watch("TeamSelected")
  @Emit("SelectTeam")
  SelectTeam() {
    return this.TeamSelected;
  }
}
</script>
<style lang="less">
.vs-select__input {
}
</style>
