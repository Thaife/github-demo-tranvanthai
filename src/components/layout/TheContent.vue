<template>
  <div class="a-content">
    <div class="a-title">
      <h2>Danh Sach Nhan Vien</h2>
      <BaseButton/>
    </div>
    <div class="a-filter">
      <div class="a-filter-option">
        <div>
          <input
            class="a-input a-input-icon"
            placeholder="Tìm kiếm theo Mã, Tên hoặc Số điện thoại"
            type="text"
            name=""
            id=""
          />
        </div>
        <div class="a-mar-0-12">
          <select class="a-combobox" name="" id="">
            <option value="">Tất cả phòng ban</option>
            <option value="">Phòng ban</option>
          </select>
        </div>
        <div>
          <select class="a-combobox" name="" id="">
            <option value="">Tất cả vị trí</option>
            <option value="">Vị trí</option>
          </select>
        </div>
      </div>
      <div class="a-filter-reset">
        <div></div>
      </div>
    </div>
    <div class="a-table-box">
      <table class="a-table">
        <thead>
          <tr>
            <th>Mã nhân viên</th>
            <th>Họ và tên</th>
            <th>Giới tính</th>
            <th class="a-text-center">Ngày sinh</th>
            <th>Điện thoại</th>
            <th>Email</th>
            <th>Chức vụ</th>
            <th>Phòng ban</th>
            <th class="a-text-right">Mức lương cơ bản</th>
            <th>Tình trạng công việc</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="employee in employees" :key="employee.EmployeeId">
            <td>{{ employee.EmployeeCode }}</td>
            <td>{{ employee.FullName }}</td>
            <td>{{ employee.GenderName }}</td>
            <td class="a-text-center">
              {{
                employee.DateOfBirth | formatDateOfBirth(employee.DateOfBirth)
              }}
            </td>
            <td>{{ employee.PhoneNumber }}</td>
            <td>{{ employee.Email }}</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="a-select-page">
      <div class="a-left">hiện thị 1-10/1000 nhân viên</div>
      <div class="a-center">
        <div class="a-first"></div>
        <div class="a-prev"></div>
        <div class="a-page-number">
          <div class="a-number">1</div>
          <div class="a-number">2</div>
          <div class="a-number">3</div>
          <div class="a-number">4</div>
        </div>
        <div class="a-next"></div>
        <div class="a-last"></div>
      </div>
      <div class="a-right">
        <span>10 nhân viên/trang</span>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import BaseButton from '../base/BaseButton.vue'

export default {
  name: "content-name",
  components: {
    BaseButton
  },
  created() {
    axios
      .get(`http://cukcuk.manhnv.net/api/v1/Employees`)
      .then((response) => {
        this.employees = response.data;
      })
      .catch(() => {
        console.log("api lỗi!");
      });
  },
  filters: {
    formatDateOfBirth(value) {
      if (value) {
        value = new Date(value)
        let dd = value.getDate();
        let mm = value.getMonth() < 9 ? "0" + value.getMonth() : value.getMonth() + 1;
        let yyyy = value.getFullYear();

        return dd + "/" + mm + "/" + yyyy;
      }
    },
  },
  data() {
    return {
      employees: [],
    };
  },
};
</script>

<style scoped>
@import url(../../style/layout/content.css);
</style>