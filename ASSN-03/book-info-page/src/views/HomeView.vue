<template>
  <div class="container">
    <h1 class="title">User Details Form</h1>
    <form v-if="showForm" @submit.prevent="submitForm">
      <div class="form-group">
        <label for="firstName">First Name:</label>
        <input type="text" class="form-control" id="firstName" v-model="firstName" />
      </div>
      <div class="form-group">
        <label for="middleName">Middle Name:</label>
        <input type="text" class="form-control" id="middleName" v-model="middleName" />
      </div>
      <div class="form-group">
        <label for="lastName">Last Name:</label>
        <input type="text" class="form-control" id="lastName" v-model="lastName" />
      </div>
      <div class="form-group">
        <label for="dob">Date of Birth:</label>
        <input type="date" class="form-control" id="dob" v-model="dob" @change="calculateAge" />
        <p v-if="age">Age: {{ age }}</p>
      </div>
      <div class="form-group">
        <label for="gender">Gender:</label>
        <div class="form-check">
          <input class="form-check-input" type="radio" name="gender" id="male" value="male" v-model="gender" />
          <label class="form-check-label" for="male">
            Male
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="radio" name="gender" id="female" value="female" v-model="gender" />
          <label class="form-check-label" for="female">
            Female
          </label>
        </div>
      </div>
      <div class="form-group">
        <label for="address">Address:</label>
        <textarea class="form-control" id="address" rows="3" v-model="address"></textarea>
      </div>
      <div class="form-group">
        <label for="education">Education:</label>
        <select class="form-control" id="education" v-model="education">
          <option value="">Select</option>
          <option value="undergraduate">Under Graduate</option>
          <option value="graduate">Graduate</option>
          <option value="postgraduate">Post Graduate</option>
        </select>
      </div>
      <button type="submit" class="btn btn-primary" :disabled="!isFormValid">Submit</button>
    </form>
    <div v-else>
      <h2>User Information</h2>
      <p>Name: {{ fullName }}</p>
      <p>Date of Birth: {{ dob }}</p>
      <p>Age: {{ age }}</p>
      <p>Gender: {{ gender }}</p>
      <p>Address: {{ address }}</p>
      <p>Education: {{ education }}</p>
      <button class="btn btn-primary" @click="showForm = true">Add New User</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showForm: true,
      firstName: '',
      middleName: '',
      lastName: '',
      dob: null,
      age: null,
      gender: '',
      address: '',
      education: '',
    };
  },
  computed
}
