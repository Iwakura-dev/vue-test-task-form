<template>
  <div>
    <div class="form-title">
      <h1>Форма для создания клиента</h1>
    </div>
    <div class="form">
      <create-client />
    </div>
  </div>
</template>

<script>
import CreateClient from "../../UI/CreateClient/CreateClient";
export default {
  name: "VuelidateForm",
  components: {
    CreateClient,
  },
};
</script>

<style lang="scss">
.form {
  display: flex;
  align-items: center;
  justify-content: center;
}

.form-container {
  box-shadow: 0px 2px 14px 2px rgba(0, 0, 0, 0.4);
  padding: 14px 26px;
  border-radius: 10px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  position: relative;
}
.form-group {
  display: flex;
  flex-direction: column;
  align-items: start;
  gap: 5px;
  & > label {
    font-size: 18px;
    padding-left: 10px;
  }
  & > label > span::after {
    content: "*";
    position: relative;
    top: 0;
    font-size: 16px;
    color: #f00;
  }
  & > input {
    border-radius: 8px;
    border: 1px solid #ccc;
    padding: 8px 16px;
    outline: none;
    font-size: 16px;
    color: #666;
    width: 400px;
  }
  & > select {
    border-radius: 8px;
    border: 1px solid #ccc;
    padding: 5px 8px;
    outline: none;
    font-size: 16px;
    color: #666;
    width: 400px;
  }
}
.clients {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.address {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.passport {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.form-submit {
  & > input {
    border: none;
    cursor: pointer;
    padding: 8px 16px;
    border-radius: 8px;
    background-color: #7a7a7a;
    color: white;
  }
}
// Text for error log
.text-danger {
  font-size: 12px;
  color: red;
}
// Adaptive layout beetwen 375px
@media screen and (max-width: 375px) {
  .form-title > h1 {
    font-size: 18px;
  }
  .form-container {
    flex-direction: column;
    padding: 8px 14px;
    gap: 10px;
  }
  .form-group {
    justify-content: center;
    align-items: center;
    & > label {
      font-size: 14px;
    }
    & > input {
      font-size: 14px;
      max-width: 220px;
      &::placeholder {
        font-size: 14px;
      }
    }
    & > select {
      max-width: 220px;
    }
  }
  .form-submit {
    & > input {
      padding: 4px 7px;
      font-size: 12px;
    }
  }
}
// Adaptive layout beetwen 375px to 425px
@media screen and (min-width: 375px) and (max-width: 425px) {
  .form-title > h1 {
    font-size: 18px;
  }
  .form-container {
    flex-direction: column;
  }
  .form-group {
    align-items: center;
    & > label {
      font-size: 16px;
    }
    & > input {
      font-size: 16px;
      max-width: max-content;
      &::placeholder {
        font-size: 16px;
      }
    }
    & > select {
      max-width: 220px;
    }
  }
}
// Adaptive layout beetwen 425px to 768px

@media screen and (min-width: 425px) and (max-width: 768px) {
  .form-title > h1 {
    font-size: 18px;
  }
  .form-container {
    flex-direction: column;
  }
  .form-group {
    align-items: center;
    & > label {
      font-size: 16px;
    }
    & > input {
      font-size: 16px;
      max-width: 100%;
      &::placeholder {
        font-size: 16px;
      }
    }
    & > select {
      max-width: 100%;
    }
  }
}
// Adaptive layout beetwen 768 px to 992px
@media screen and (min-width: 768px) and (max-width: 992px) {
  .form-title > h1 {
    font-size: 18px;
  }
  .form-container {
    width: 80vh;
    flex-direction: column;
  }
  .form-group {
    align-items: center;
    & > label {
      font-size: 16px;
    }
    & > input {
      font-size: 16px;
      max-width: 100%;
      &::placeholder {
        font-size: 16px;
      }
    }
    & > select {
      max-width: 100%;
    }
  }
}
</style>
