# Engineer-school
IT school web site
import React, { useState } from 'react';
import { motion } from 'framer-motion';
import { Card, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { FaPython, FaLaptopCode, FaLock } from 'react-icons/fa';
import { Input } from '@/components/ui/input';

export default function HomePage() {
  const [form, setForm] = useState({ name: '', email: '', message: '' });
  const [submitted, setSubmitted] = useState(false);

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    if (form.name && form.email && form.message) {
      setSubmitted(true);
    } else {
      alert('Пожалуйста, заполните все поля.');
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-r from-gray-900 to-black text-white overflow-x-hidden">
      {/* Header */}
      <header className="flex items-center justify-between p-6 shadow-2xl bg-black bg-opacity-80 sticky top-0 z-50">
        <div className="flex items-center gap-4">
          <img src="/ENGINEER%20SCHOOL-2.png" alt="Engineer School Logo" className="w-16 h-16 animate-pulse" />
          <h1 className="text-3xl font-extrabold bg-gradient-to-r from-red-500 to-yellow-500 bg-clip-text text-transparent">Engineer School</h1>
        </div>
        <nav className="space-x-6 text-lg">
          <a href="#courses" className="hover:text-red-500 transition duration-300">Курсы</a>
          <a href="#about" className="hover:text-red-500 transition duration-300">О нас</a>
          <a href="#contact" className="hover:text-red-500 transition duration-300">Контакты</a>
        </nav>
      </header>

      {/* Hero Section */}
      <section className="flex flex-col items-center justify-center text-center py-40 px-4 relative">
        <motion.h2 
          initial={{ opacity: 0, y: -50 }} 
          animate={{ opacity: 1, y: 0 }} 
          transition={{ duration: 1 }} 
          className="text-5xl font-extrabold mb-6 bg-gradient-to-r from-blue-400 to-purple-600 bg-clip-text text-transparent"
        >
          Добро пожаловать в будущее IT
        </motion.h2>
        <motion.p 
          initial={{ opacity: 0 }} 
          animate={{ opacity: 1 }} 
          transition={{ delay: 0.5, duration: 1 }} 
          className="max-w-2xl mb-8 text-gray-300"
        >
          Учебный центр для инженеров, программистов и всех, кто хочет прокачать свои digital-навыки.
        </motion.p>
        <motion.div whileHover={{ scale: 1.1 }}>
          <Button size="lg" className="text-lg bg-red-500 hover:bg-red-600 transition duration-300">Записаться на курс</Button>
        </motion.div>

        <motion.div 
          className="absolute top-0 left-0 w-full h-full bg-gradient-to-br from-red-500 to-transparent opacity-10 rounded-full blur-3xl"
          animate={{ scale: [1, 1.2, 1] }}
          transition={{ duration: 6, repeat: Infinity }}
        />
      </section>

      {/* Courses Section */}
      <section id="courses" className="py-20 px-6">
        <h3 className="text-4xl font-bold text-center mb-12">Наши Курсы</h3>
        <div className="grid md:grid-cols-3 gap-8">
          {[
            { name: 'Python', icon: <FaPython size={40} /> },
            { name: 'Web-разработка', icon: <FaLaptopCode size={40} /> },
            { name: 'Кибербезопасность', icon: <FaLock size={40} /> },
          ].map((course, idx) => (
            <motion.div 
              key={idx}
              whileHover={{ scale: 1.05, rotate: [0, 2, -2, 0] }}
            >
              <Card className="bg-gray-800 rounded-2xl shadow-xl border border-gray-700">
                <CardContent className="p-6 flex flex-col items-center">
                  <div className="text-red-500 mb-4">{course.icon}</div>
                  <h4 className="text-2xl font-bold mb-4">{course.name}</h4>
                  <p className="text-gray-400 text-center">Углубленные модули + практика на реальных проектах.</p>
                </CardContent>
              </Card>
            </motion.div>
          ))}
        </div>
      </section>

      {/* About Section */}
      <section id="about" className="py-20 px-6 bg-gray-900 relative">
        <motion.h3 
          whileInView={{ scale: 1.1 }} 
          transition={{ duration: 0.5 }}
          className="text-4xl font-bold text-center mb-12"
        >
          О нас
        </motion.h3>
        <div className="max-w-4xl mx-auto text-center text-gray-300">
          Мы — команда профессионалов с опытом в IT более 10 лет. Наша миссия — сделать инженерные и цифровые профессии доступными каждому.
        </div>

        <motion.div 
          className="absolute top-0 right-0 w-80 h-80 bg-purple-500 opacity-20 rounded-full blur-3xl"
          animate={{ scale: [1, 1.2, 1] }}
          transition={{ duration: 8, repeat: Infinity }}
        />
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-20 px-6">
        <h3 className="text-4xl font-bold text-center mb-12">Контакты</h3>
        <motion.div 
          whileHover={{ scale: 1.05 }} 
          className="max-w-2xl mx-auto text-center"
        >
          <p className="mb-4">Email: info@engineerschool.com</p>
          <p className="mb-4">Телефон: +998 90 123 45 67</p>
        </motion.div>

        {/* Contact Form */}
        {submitted ? (
          <p className="text-green-500 text-center text-xl mt-8">Спасибо за заявку! Мы свяжемся с вами.</p>
        ) : (
          <form onSubmit={handleSubmit} className="max-w-2xl mx-auto mt-8 space-y-4">
            <Input 
              type="text" 
              name="name" 
              placeholder="Ваше имя" 
              value={form.name} 
              onChange={handleChange} 
              className="p-4 bg-gray-800 border border-gray-700 rounded-xl w-full"
            />
            <Input 
              type="email" 
              name="email" 
              placeholder="Ваш email" 
              value={form.email} 
              onChange={handleChange} 
              className="p-4 bg-gray-800 border border-gray-700 rounded-xl w-full"
            />
            <textarea 
              name="message" 
              placeholder="Ваше сообщение" 
              value={form.message} 
              onChange={handleChange} 
              rows="4"
              className="p-4 bg-gray-800 border border-gray-700 rounded-xl w-full"
            ></textarea>
            <Button type="submit" size="lg" className="bg-blue-500 hover:bg-blue-600 transition duration-300 w-full">Отправить</Button>
          </form>
        )}
      </section>

      {/* Footer */}
      <footer className="py-6 text-center text-gray-500 border-t border-gray-700">
        © 2025 Engineer School. Все права защищены.
      </footer>
    </div>
  );
}
