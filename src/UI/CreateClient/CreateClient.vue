<template>
  <form @submit.prevent="handleSubmit">
    <div class="form-container">
      <!-- Form has lastname -->
      <div class="clients">
        <div class="form-group">
          <label for="lastname">
            <span>Фамилия</span>
          </label>
          <input
            type="text"
            name=""
            id="lastname"
            class="form-control"
            v-model="form.personal_data.lastname"
            placeholder="Введите свою фамилию"
          />
          <span
            v-if="
              !$v.form.personal_data.lastname.required &&
              $v.form.personal_data.lastname.$dirty
            "
            class="text-danger"
            >Фамилия обязательно к заполнению!</span
          >
          <span
            v-if="
              !$v.form.personal_data.lastname.alpha &&
              $v.form.personal_data.lastname.$dirty
            "
            class="text-danger"
          ></span>
        </div>
        <!-- Form has name -->
        <div class="form-group">
          <label for="name">
            <span>Имя</span>
          </label>
          <input
            type="text"
            name=""
            id="name"
            class="form-control"
            v-model="form.personal_data.name"
            placeholder="Введите свое имя"
          />
          <span
            v-if="
              !$v.form.personal_data.name.required &&
              $v.form.personal_data.name.$dirty
            "
            class="text-danger"
            >Имя обязательно к заполнению!</span
          >
          <span
            v-if="
              !$v.form.personal_data.name.alpha &&
              $v.form.personal_data.name.$dirty
            "
            class="text-danger"
          ></span>
        </div>
        <!-- Form has surname -->
        <div class="form-group">
          <label for="surname">Отчество</label>
          <input
            type="text"
            name=""
            id="surname"
            class="form-control"
            v-model="form.personal_data.surname"
            placeholder="Введите свое отчество"
          />
        </div>
        <!-- Form has date birthday -->
        <div class="form-group">
          <label for="date-birthday"><span>День рождения</span></label>
          <input
            type="date"
            name=""
            id="date-birthday"
            v-model="form.personal_data.date_birthday"
          />
          <span
            v-if="
              !$v.form.personal_data.date_birthday.required &&
              $v.form.personal_data.date_birthday.$dirty
            "
            class="text-danger"
            >Дата обязательна к заполнению!</span
          >
        </div>
        <!-- Form has phone number -->
        <div class="form-group">
          <label for="phone-number"><span>Номер телефона</span></label>
          <input
            type="tel"
            name=""
            id="phone-number"
            placeholder="Введите свой номер телефона"
            v-model="form.personal_data.phone_number"
          />
          <span
            v-if="
              (!$v.form.personal_data.phone_number.minLength ||
                !$v.form.personal_data.phone_number.required) &&
              $v.form.personal_data.phone_number.$dirty
            "
            class="text-danger"
            >Номер телефона обязателен к заполнению!</span
          >
        </div>
        <!-- Form has gender -->
        <div class="form-group">
          <label for="gender">Пол</label>
          <select v-model="form.personal_data.gender" id="gender">
            <option
              v-for="(genders, index) in ['Мужской', 'Женский']"
              :key="index"
            >
              {{ genders }}
            </option>
          </select>
        </div>
        <!-- Form has group clients -->
        <multiple-select :groupClients="form.personal_data.group_clients" />
        <!-- Form has current doctor -->
        <div class="form-group">
          <label for="doctor">Лечащий врач</label>
          <select v-model="form.personal_data.current_doctor" id="doctor">
            <option
              v-for="(doctor, index) in ['Иванов', 'Захаров', 'Чернышева']"
              :key="index"
            >
              {{ doctor }}
            </option>
          </select>
        </div>
        <!-- Form has don't send sms -->
        <div class="form-group">
          <label>Не отправлять смс</label>
          <input
            type="checkbox"
            name=""
            id=""
            v-model="form.personal_data.dont_send_sms"
          />
        </div>
      </div>
      <!-- Address -->
      <div class="address">
        <!-- Form Elements has index -->
        <div class="form-group">
          <label for="index">Индекс</label>
          <input
            type="number"
            name=""
            id="index"
            placeholder="Впишите свой почтовый индекс"
            v-model="form.address.index"
          />
        </div>
        <!-- Form Elements has Country -->
        <div class="form-group">
          <label for="country">Страна</label>
          <input
            type="text"
            name=""
            id="country"
            placeholder="Впишите название своей страны"
            v-model="form.address.country"
          />
        </div>
        <!-- Form Elements has Area -->
        <div class="form-group">
          <label for="area">Область</label>
          <input
            type="text"
            name=""
            id="area"
            placeholder="Впишите в какой области проживаете"
            v-model="form.address.area"
          />
        </div>
        <!-- Form Elements has City -->
        <div class="form-group">
          <label for="city"><span>Город</span></label>
          <input
            type="text"
            name=""
            id="city"
            placeholder="Впишите название своего города"
            v-model="form.address.city"
          />
          <span
            v-if="!$v.form.address.city.required && $v.form.address.city.$dirty"
            class="text-danger"
            >Город обязателен к заполнению!</span
          >
          <span
            v-if="!$v.form.address.city.alpha && $v.form.address.city.$dirty"
            class="text-danger"
          ></span>
        </div>
        <!-- Form Elements has Street  -->
        <div class="form-group">
          <label for="street">Улица</label>
          <input
            type="text"
            name=""
            id="street"
            placeholder="Впишите в какой улице вы проживаете"
            v-model="form.address.street"
          />
        </div>
        <!-- Form Elements has House  -->
        <div class="form-group">
          <label for="house">Дом</label>
          <input
            type="text"
            name=""
            id="house"
            placeholder="Впишите в каком доме вы проживаете"
            v-model="form.address.house"
          />
        </div>
      </div>
      <!-- Passport -->
      <div class="passport">
        <!-- Form Elements has type documents -->
        <div class="form-group">
          <label for="type_documents"><span>Тип документа</span></label>
          <select v-model="form.passport.type_documents">
            <option
              v-for="(documents, index) in [
                'Паспорт',
                'Свидетельство о рождении',
                'Вод.удостоверение',
              ]"
              :value="documents"
              :key="index"
            >
              {{ documents }}
            </option>
          </select>
          <span
            v-if="
              !$v.form.passport.type_documents.required &&
              $v.form.personal_data.date_birthday.$dirty
            "
            class="text-danger"
            >Тип документа обязателен к заполнению!</span
          >
        </div>
        <!-- Form Elements has series -->
        <div class="form-group">
          <label for="series">Серия</label>
          <input
            type="text"
            name=""
            id="series"
            placeholder="Впишите серию своего документа"
            v-model="form.passport.series"
          />
        </div>
        <!-- Form Elements has number -->
        <div class="form-group">
          <label for="number">Номер</label>
          <input
            type="number"
            name=""
            id="number"
            v-model="form.passport.number"
            placeholder="Впишите номер своего документа"
          />
        </div>
        <!-- Form Elements has who issued-->
        <div class="form-group">
          <label for="who_issued">Кем выдан</label>
          <input
            type="text"
            name=""
            id="who_issued"
            v-model="form.passport.who_issued"
            placeholder="Впишите кем был выдан документ"
          />
        </div>
        <!-- Form Elements has date of issue -->
        <div class="form-group">
          <label for="date_of_issue"><span>Дата выдачи</span></label>
          <input
            type="date"
            name=""
            id=""
            v-model="form.passport.date_of_issue"
          />
          <span
            v-if="
              !$v.form.passport.date_of_issue.required &&
              $v.form.passport.date_of_issue.$dirty
            "
            class="text-danger"
            >Дата выдачи обязательна к заполнению!</span
          >
        </div>
        <!-- Form Submit -->
        <div class="form-submit">
          <input type="submit" value="Отправить заявку на создание клиента" />
        </div>
      </div>
    </div>
  </form>
</template>

<script>
import { required, minLength, alpha } from "vuelidate/lib/validators";
import MultipleSelect from "../MultipleSelect/MultipleSelect.vue";
export default {
  name: "CreateClient",
  components: {
    MultipleSelect,
  },
  data() {
    return {
      form: {
        personal_data: {
          name: "",
          lastname: "",
          surname: "",
          date_birthday: "",
          phone_number: "",
          gender: "",
          group_clients: [],
          current_doctor: "",
          dont_send_sms: false,
        },
        address: {
          index: "",
          country: "",
          area: "",
          city: "",
          street: "",
          house: "",
        },
        passport: {
          type_documents: "",
          series: "",
          number: "",
          who_issued: "",
          date_of_issue: "",
        },
      },
    };
  },
  validations: {
    form: {
      personal_data: {
        name: { required, alpha },
        lastname: { required },
        date_birthday: { required },
        phone_number: { required, minLength: minLength(11) },
      },
      address: {
        city: { required, alpha },
      },
      passport: {
        type_documents: { required },
        date_of_issue: { required },
      },
    },
  },
  methods: {
    handleSubmit() {
      this.$v.$touch();
      if (!this.$v.$invalid) {
        alert("Новый клиент успешно создан!");
      }
    },
  },
};
</script>

<styles lang="scss" scoped></styles>
