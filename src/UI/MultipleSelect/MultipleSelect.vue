<template>
  <div id="multiple-select">
    <section class="section_top" id="registration">
      <form class="createMultiselect" name="" action="">
        <div class="createMultiselect_inner">
          <div class="form_label">
            <span class="form_text">Группа клиентов</span>

            <div class="multiselect_block">
              <label for="select-2" class="field_multiselect"
                >Выберите группу клиента</label
              >
              <input
                id="checkbox-2"
                class="multiselect_checkbox"
                type="checkbox"
              />
              <label for="checkbox-2" class="multiselect_label"></label>
              <select
                id="select-2"
                class="field_select"
                name="frameworks"
                v-model="$props.groupClients"
                required
                multiple
              >
                <option
                  v-for="(items, index) in ['VIP', 'Проблемные', 'ОМС']"
                  :key="index"
                  :value="items"
                >
                  {{ items }}
                </option>
              </select>
            </div>
          </div>
        </div>
      </form>
    </section>
  </div>
</template>

<script>
export default {
  name: "MultipleSelect",
  props: {
    groupClients: Array,
  },
};
</script>

<styles scoped lang="scss">
.createMultiselect_inner {
  position: relative;
  width: 100%;
}

.form_text {
  display: flex;
  justify-content: center;
  margin-bottom: 6px;
  font-size: 18px;
  line-height: 16px;
}

.form_text::after {
  content: "*";
  position: relative;
  top: 0;
  font-size: 14px;
  color: #f00;
}
.form_label {
  display: flex;
  flex-direction: column;
  align-items: start;
  gap: 5px;
}
.form_label input,
.field_multiselect {
  position: relative;
  width: 100%;
  text-align: start;
  display: block;
  border: 1px solid #ccc;
  box-sizing: border-box;
  border-radius: 8px;
  padding: 12px 40px 10px 16px;
  font-size: 14px;
  color: #ccc;

  outline-color: #ccc;

  &::placeholder {
    color: #ccc;
  }
  &:hover {
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.16);
  }
  &:focus {
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.16);
  }
}

.field_multiselect_help {
  font-size: 14px;
}

.multiselect_block {
  position: relative;
  width: 100%;
}
.field_select {
  width: 100%;
  border: 1px solid #ccc;
  border-bottom-right-radius: 22px;
  border-bottom-left-radius: 22px;
  box-sizing: border-box;
  z-index: 6;
}

.field_select[multiple] {
  overflow-y: auto;
}

.field_select option {
  display: block;
  padding: 8px 16px;
  width: 100%;
  cursor: pointer;
  &:checked {
    background-color: #eceff3;
  }
  &:hover {
    background-color: #d5e8fb;
  }
}

.multiselect_label {
  position: absolute;
  top: 1px;
  left: 2px;
  width: 100%;
  height: 44px;
  cursor: pointer;
  z-index: 3;
}

.field_select {
  display: none;
}

input.multiselect_checkbox {
  position: absolute;
  right: 0;
  top: 0;
  width: 40px;
  height: 40px;
  border: none;
  opacity: 0;
}

.multiselect_checkbox:checked ~ .field_select {
  display: block;
}

.multiselect_checkbox:checked ~ .field_multiselect_help {
  opacity: 1;
}
@media screen and (max-width: 375px) {
  .createMultiselect_inner {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .form_text {
    font-size: 14px;
  }
  .form_label {
    align-items: center;
  }
  .field_select {
    width: 100%;
  }
}
@media screen and (min-width: 375px) and (max-width: 425px) {
  .createMultiselect_inner {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .form_text {
    font-size: 16px;
  }
  .form_label {
    align-items: center;
  }
}
@media screen and (min-width: 425px) and (max-width: 768px) {
  .createMultiselect_inner {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .form_text {
    font-size: 16px;
  }
  .form_label {
    align-items: center;
    width: 100%;
  }
}
@media screen and (min-width: 768px) and (max-width: 992px) {
  .createMultiselect_inner {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .form_text {
    font-size: 16px;
  }
  .form_label {
    align-items: center;
    width: 70%;
  }
}
</styles>
