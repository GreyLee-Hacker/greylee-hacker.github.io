<template>
  <div class="container">
    <aside class="sidebar">
      <div class="profile-image-container">
        <img alt="个人照片" src="./assets/证件照.jpg" class="profile-image">
      </div>
      <h2 class="name">李光毅</h2>
      <p class="title">中国人民大学2023级本科生</p>
      <div class="bio">
        <p>2023年9月考入中国人民大学图灵实验班，主修计算机科学与技术。</p>
        <p>对人工智能、数据分析等领域有浓厚兴趣，掌握C/C++、Python、Web开发等技术，并在此基础上进行了一些应用开发。</p>
        <p>本人目前有创业想法，正在寻找志同道合的伙伴，希望可以一起做出一些有意义的事情。</p>
      </div>
      <nav class="sidebar-nav">
        <a href="#about">关于我</a>
        <a href="#projects">项目</a>
        <a @click.prevent="openContactModal">联系方式</a>
      </nav>
    </aside>
    <main class="main-content">
      <h1>欢迎来到我的个人网站</h1>

      <section class="projects">
        <h2>项目展示</h2>
        <div class="project-grid">
          <div class="project-card" v-for="project in projects" :key="project.id">
            <h3>{{ project.name }}</h3>
            <p>{{ project.description }}</p>
            <div class="tech-stack">
              <span v-for="tech in project.technologies" :key="tech">{{ tech }}</span>
            </div>
            <div class="project-link">
              <a :href="project.link" target="_blank" rel="noopener noreferrer">查看项目</a>
            </div>
          </div>
        </div>
      </section>

      <!-- 在这里添加主要内容 -->
    </main>
    <div v-if="showContactModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="showContactModal = false">&times;</span>
        <h2>联系方式</h2>
        <p>邮箱：2829604235@qq.com</p>
        <p>微信：LGY_LGX</p>
        <p>电话：+86 132 1033 6719</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      showContactModal: false,
      projects: [
        {
          id: 1,
          name: "智能聊天机器人 （当然是假的，只是为了好玩）",
          description: "基于深度学习的智能对话系统，能够理解和回应复杂的用户查询。",
          technologies: ["Python", "TensorFlow", "NLP"],
          link: "https://github.com/yourusername/chatbot-project"
        },
        // ... 更多项目
      ]
    }
  },
  methods: {
    openContactModal() {
      this.showContactModal = true;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap');
@import './assets/提示框.css';

body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: 'Roboto', sans-serif;
  background-color: #f4f4f4;
}

#app {
  height: 100%;
}

.container {
  display: flex;
  height: 100%;
}

.sidebar {
  width: 300px;
  background-color: #2c3e50;
  color: #ecf0f1;
  padding: 30px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.profile-image-container {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  overflow: hidden;
  margin-bottom: 20px;
  border: 4px solid #ecf0f1;
}

.profile-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.name {
  font-size: 24px;
  font-weight: 700;
  margin: 10px 0;
}

.title {
  font-size: 16px;
  color: #bdc3c7;
  margin-bottom: 20px;
}

.bio {
  text-align: center;
  font-size: 14px;
  line-height: 1.6;
  margin-bottom: 30px;
}

.sidebar-nav {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.sidebar-nav a {
  color: #ecf0f1;
  text-decoration: none;
  padding: 10px;
  margin: 5px 0;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.sidebar-nav a:hover {
  background-color: #34495e;
}

.main-content {
  flex: 1;
  padding: 40px;
  overflow-y: auto;
}

h1 {
  color: #2c3e50;
  font-size: 32px;
  margin-bottom: 20px;
}

.projects {
  margin-top: 40px;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.project-card {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.tech-stack {
  margin-top: 10px;
  margin-bottom: 15px;
  /* 增加底部边距 */
}

.tech-stack span {
  background-color: #e9ecef;
  padding: 3px 8px;
  border-radius: 4px;
  font-size: 0.8em;
  margin-right: 5px;
  margin-bottom: 5px;
  /* 为多行技术标签添加底部间距 */
  display: inline-block;
  /* 使 margin-bottom 生效 */
}

.project-link {
  margin-top: 15px;
  /* 为链接添加顶部边距 */
}

.project-link a {
  display: inline-block;
  padding: 8px 15px;
  background-color: #3498db;
  color: white;
  text-decoration: none;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.project-link a:hover {
  background-color: #2980b9;
}
</style>
