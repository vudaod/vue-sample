 <template>
  <div class="center grid">
    <vs-row>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="4">
        <AbsenceTypes @SelectAbsenceTypes="addAbsenceTypes"></AbsenceTypes>
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="6">
        <Filters
          @SelectLocation="addLocation"
          @SelectDepartment="addDepartment"
          @SelectTeam="addTeam"
        ></Filters>
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="2">
        <BookAbsenceButton></BookAbsenceButton>
      </vs-col>
    </vs-row>
    <br />
    <vs-row>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="12">
        <div class="chip" v-for="item in AbsenceTypes" :key="item.index">
          {{ item }}
          <span class="closebtn" onclick="this.parentElement.remove()"
            >&times;</span
          >
        </div>
        <div :style="{ background: '#37D8AB' }" v-if="Location" class="chip">
          {{ Location }}
          <span class="closebtn" @click="removeLocation">&times;</span>
        </div>
        <div :style="{ background: '#027FCE' }" v-if="Department" class="chip">
          {{ Department }}
          <span class="closebtn" @click="removeDepartment">&times;</span>
        </div>
        <div :style="{ background: '#B5173B' }" v-if="Team" class="chip">
          {{ Team }}
          <span class="closebtn" @click="removeTeam">&times;</span>
        </div>
      </vs-col>
    </vs-row>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import AbsenceTypes from "@/components/AbsenceTypes.vue"; // @ is an alias to /src
import Filters from "@/components/Filters.vue"; // @ is an alias to /src
import BookAbsenceButton from "@/components/BookAbsenceButton.vue";
@Component({
  components: {
    AbsenceTypes,
    Filters,
    BookAbsenceButton,
    FiltersResult,
  },
})
export default class FiltersResult extends Vue {
  private AbsenceTypes: Array<string> = [];
  private Location: string = "";
  private Department: string = "";
  private Team: string = "";

  removeLocation(e: any) {
    this.Location = "";
  }
  removeDepartment(e: any) {
    this.Department = "";
  }
  removeTeam(e: any) {
    this.Team = "";
  }
  addAbsenceTypes(item: any) {
    this.AbsenceTypes = item.filter((i: string) => i);
  }
  addLocation(item: any) {
    this.Location = item;
  }
  addDepartment(item: any) {
    this.Department = item;
  }
  addTeam(item: any) {
    this.Team = item;
  }
}
</script>
<style lang="less">
.chip {
  display: inline-block;
  padding: 0px 8px;
  margin-right: 5px;
  position: static;
  width: 130px;
  height: 24px;
  left: 0px;
  background-color: #ff9d6f;
  border-radius: 4px;
  color: #fff;
  text-align: left;
  padding-top: 6px;
}
.closebtn {
  padding-left: 10px;
  color: #fff;
  font-weight: bold;
  float: right;
  font-size: 18px;
  cursor: pointer;
}

.closebtn:hover {
  color: #000;
}
</style>
