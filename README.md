# M-KBounceHouseTEST.github.io
// App.jsx
import React from 'react';
import BookingForm from './components/BookingForm';
import CalendarView from './components/CalendarView';
import { Card, CardContent } from '@/components/ui/card';
import { motion } from 'framer-motion';

export default function App() {
  return (
    <main className="min-h-screen bg-gradient-to-br from-blue-100 to-pink-100 p-6">
      <div className="max-w-5xl mx-auto space-y-8">
        <motion.h1
          className="text-4xl font-bold text-center text-purple-800"
          initial={{ opacity: 0, y: -20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.6 }}
        >
          M&K Bouncy Houses Booking
        </motion.h1>

        <Card className="bg-white shadow-xl rounded-2xl">
          <CardContent className="p-6">
            <CalendarView />
          </CardContent>
        </Card>

        <Card className="bg-white shadow-xl rounded-2xl">
          <CardContent className="p-6">
            <BookingForm />
          </CardContent>
        </Card>

        <footer className="text-center text-sm text-gray-600">
          © 2025 M&K Bouncy Houses | Mark & Kelsey Galan | 774-301-6499 / 774-770-8057
        </footer>
      </div>
    </main>
  );
}

// components/CalendarView.jsx
import React from 'react';

export default function CalendarView() {
  return (
    <div>
      <h2 className="text-xl font-semibold text-purple-700 mb-4">Available Booking Dates (Weekends Only)</h2>
      <p className="text-sm text-gray-600">*Calendar integration coming soon. This placeholder will show clickable available weekends for booking.</p>
    </div>
  );
}

// components/BookingForm.jsx
import React, { useState } from 'react';

export default function BookingForm() {
  const [form, setForm] = useState({
    name: '',
    date: '',
    time: '',
    phone: '',
    address: '',
    houseType: 'Castle'
  });

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    // Here you'd add address validation for "Bristol, MA"
    // and payment integration for the $50 deposit
    alert(`Booking submitted: ${JSON.stringify(form)}`);
  };

  return (
    <form className="space-y-4" onSubmit={handleSubmit}>
      <h2 className="text-xl font-semibold text-purple-700">Book Your Bouncy House</h2>
      <input type="text" name="name" placeholder="Full Name" onChange={handleChange} className="w-full p-2 border rounded" required />
      <input type="text" name="address" placeholder="Bristol, MA Address" onChange={handleChange} className="w-full p-2 border rounded" required />
      <input type="date" name="date" onChange={handleChange} className="w-full p-2 border rounded" required />
      <input type="time" name="time" onChange={handleChange} className="w-full p-2 border rounded" required />
      <input type="tel" name="phone" placeholder="Call Back Number" onChange={handleChange} className="w-full p-2 border rounded" required />
      <select name="houseType" onChange={handleChange} className="w-full p-2 border rounded">
        <option value="Castle">Castle Themed Bouncy House</option>
        <option value="Jungle">Jungle Themed Bouncy House</option>
      </select>
      <button type="submit" className="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">Submit $50 Deposit & Book</button>
    </form>
  );
}

