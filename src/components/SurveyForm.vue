<template>
  <div class="background">
    <div class="survey-container">
      <h1>Опрос от "Экспресс Букет"</h1>

      <div class="question">
        <label>1. Насколько вероятно, что вы порекомендуете нас друзьям и знакомым?</label>
        <input 
          type="range" 
          min="0" 
          max="10" 
          v-model="ratings.recommend" 
          class="rating-slider"
        />
        <div class="rating-value">{{ ratings.recommend }}</div>
      </div>

      <div class="question">
        <label>2. Что вам понравилось или не понравилось у нас?</label>
        <textarea v-model="feedback" placeholder="Ваши комментарии..."></textarea>
      </div>

      <div class="question">
        <label>3. Хотели бы вы прийти к нам еще?</label>
        <input 
          type="range" 
          min="0" 
          max="10" 
          v-model="ratings.comeAgain" 
          class="rating-slider"
        />
        <div class="rating-value">{{ ratings.comeAgain }}</div>
      </div>

      <button class="submit" @click="submitSurvey">Отправить</button>
      
      <div v-if="submitted" class="thank-you-message">
        Спасибо за ваши ответы!
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      ratings: {
        recommend: 5,
        comeAgain: 5,
      },
      feedback: '',
      submitted: false,
    };
  },
  methods: {
    async submitSurvey() {
      try {
        // Отправка данных на сервер с использованием axios
        await axios.post('https://your-server-api-url.com/survey', {
          recommend: this.ratings.recommend,
          feedback: this.feedback,
          comeAgain: this.ratings.comeAgain,
        });
        // Отметить опрос как отправленный после успешного ответа
        this.submitted = true;
      } catch (error) {
        console.error('Ошибка отправки данных:', error);
        alert('Ошибка при отправке данных. Пожалуйста, попробуйте еще раз.');
      }
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');

.background {
  background-color: #b0b0b0;
  padding: 50px;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.survey-container {
  max-width: 800px;
  width: 100%;
  padding: 40px;
  border-radius: 15px;
  background-color: rgba(42, 42, 42, 0.95);
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.9);
  font-family: 'Lobster', cursive;
  color: #e0e0e0;
  transition: transform 0.3s;
  font-size: 1.3em;
}

@media (max-width: 600px) {
  .survey-container {
    padding: 20px;
    font-size: 1em;
  }

  h1 {
    font-size: 1.5em;
  }

  .submit {
    width: 100%;
  }

  .rating-slider {
    height: 10px;
  }

  .rating-slider::-webkit-slider-thumb,
  .rating-slider::-moz-range-thumb {
    width: 20px;
    height: 20px;
  }
}

.survey-container:hover {
  transform: scale(1.02);
}

h1 {
  text-align: center;
  color: #f5f5f5;
  margin-bottom: 20px;
  text-shadow: 3px 3px 8px rgba(0, 0, 0, 0.8);
}

.question {
  margin-bottom: 30px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.3);
  padding-bottom: 15px;
}

label {
  font-weight: bold;
  display: block;
  margin-bottom: 10px;
  color: #f5f5f5;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
}

.rating-slider {
  width: 100%;
  appearance: none;
  height: 15px;
  border-radius: 5px;
  background: #444;
  transition: background 0.3s ease;
}

.rating-slider:hover {
  background: #555;
}

.rating-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #ffcc00;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.rating-slider::-moz-range-thumb {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #ffcc00;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.rating-value {
  text-align: center;
  font-weight: bold;
  margin-top: 10px;
}

textarea {
  width: 100%;
  height: 120px;
  border: 1px solid #666;
  border-radius: 5px;
  padding: 10px;
  resize: none;
  font-family: 'Lobster', cursive;
  background-color: #333;
  color: #f5f5f5;
  transition: border-color 0.3s ease;
}

textarea:focus {
  border-color: #ffcc00;
}

.submit {
  padding: 15px 25px;
  background-color: #ffcc00;
  color: #2a2a2a;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 18px;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.submit:hover {
  background-color: #e6b800;
  transform: scale(1.05);
}

.thank-you-message {
  margin-top: 20px;
  text-align: center;
  color: #ffcc00;
  font-weight: bold;
  font-size: 1.5em;
}
</style>
