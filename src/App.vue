<template>
  <div class="container">
    <h1>Jadwal Pelajaran</h1>
    <div class="schedule">
      <div v-for="(day, index) in days" :key="index" class="grid-item">
        <h2>{{ day.name }}</h2>
        <ul>
          <li v-for="(subject, idx) in day.subjects" :key="idx" class="subject">
            <span :class="{ done: subject.done }">{{ subject.name }}</span>
            <input type="text" v-model="subject.name" />
            <button @click="toggleStatus(day, idx)">{{ subject.done ? 'Batal' : 'Selesai' }}</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      days: [
        { name: "Senin", subjects: [{ name: "Matematika", done: false }, { name: "Bahasa Indonesia", done: false }] },
        { name: "Selasa", subjects: [{ name: "IPA", done: false }, { name: "Bahasa Inggris", done: false }] },
        { name: "Rabu", subjects: [{ name: "IPS", done: false }, { name: "PKN", done: false }] },
        { name: "Kamis", subjects: [{ name: "Olahraga", done: false }, { name: "Seni", done: false }] },
        { name: "Jumat", subjects: [{ name: "Agama", done: false }, { name: "TIK", done: false }] },
      ],
    };
  },
  methods: {
    toggleStatus(day, idx) {
      day.subjects[idx].done = !day.subjects[idx].done;
    },
  },
};
</script>

<style>
.container {
  max-width: 800px;
  margin: auto;
  padding: 20px;
  text-align: center;
}
body {
  background-image: url(./src/assets/ml.jpg);
  background-size: cover;
  background-position: center;
}

.schedule {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.grid-item {
  background-color: #f9f9f9;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.grid-item h2 {
  margin-bottom: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

.subject {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

.subject input[type="text"] {
  margin-left: auto;
}

.done {
  text-decoration: line-through;
}
</style>