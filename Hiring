import { useState } from "react";

export default function RecruitmentLandingPage() {
  const [form, setForm] = useState({
    nama: "",
    usia: "",
    kota: "",
    instagram: "",
    whatsapp: "",
    motivasi: ""
  });
  const [error, setError] = useState({});
  const [showNotification, setShowNotification] = useState(false);

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
    setError({ ...error, [e.target.name]: "" });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    let newError = {};
    if (!form.nama) newError.nama = "Tolong isi data ini";
    if (!form.usia) newError.usia = "Tolong isi data ini";
    if (!form.kota) newError.kota = "Tolong isi data ini";
    if (!form.whatsapp) newError.whatsapp = "Tolong isi data ini";
    if (!form.motivasi) newError.motivasi = "Tolong isi data ini";

    if (Object.keys(newError).length > 0) {
      setError(newError);
      setShowNotification(true);
      return;
    }

    setShowNotification(false);

    // Kirim data ke Google Form
    const formUrl = "https://docs.google.com/forms/d/e/1FAIpQLSdyRUYOMX8e6jlgQK7nY3cWq7nKvBtsqWehdGoYNMRUYtI2WA/formResponse";
    const formData = new FormData();
    formData.append("entry.1855505122", form.nama); // Nama Lengkap
    formData.append("entry.1782272456", form.usia); // Usia
    formData.append("entry.1870722159", form.kota); // Kota
    formData.append("entry.1569487914", form.instagram); // Instagram
    formData.append("entry.1216670540", form.whatsapp); // WhatsApp
    formData.append("entry.2112859902", form.motivasi); // Motivasi

    fetch(formUrl, {
      method: "POST",
      mode: "no-cors",
      body: formData,
    })
      .then(() => {
        const message = `Halo, saya ${form.nama}, usia ${form.usia} dari ${form.kota}, ingin join tim kamu. Motivasi saya: ${form.motivasi}`;
        const whatsappURL = `https://wa.me/62${form.whatsapp.replace(/^0/, "").replace(/[^0-9]/g, "")}?text=${encodeURIComponent(message)}`;
        window.location.href = whatsappURL;
      })
      .catch((err) => {
        alert("Terjadi kesalahan saat mengirim data. Silakan coba lagi.");
        console.error(err);
      });
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-green-100 to-white text-gray-800 p-4">
      {showNotification && (
        <div className="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded mb-6 text-center max-w-3xl mx-auto">
          Harap mengisi semua data pada form
        </div>
      )}
      <header className="text-center py-10">
        <h1 className="text-4xl font-bold mb-2">Gabung Bareng Tim Gue 💼</h1>
        <p className="text-lg text-gray-600 max-w-xl mx-auto">
          Bangun karier & income bareng di industri keuangan modern, buat kamu yang ambisius dan open sama peluang baru
        </p>
      </header>

      <section className="max-w-3xl mx-auto bg-white shadow-xl rounded-2xl p-6 md:p-10 mb-8">
        <h2 className="text-2xl font-semibold mb-4">Kenapa Gabung Bareng Kita?</h2>
        <ul className="space-y-3 text-gray-700">
          <li>✅ Dimentorin langsung & kerja bareng tim yang supportive</li>
          <li>✅ Waktu fleksibel, bisa part-time sambil kuliah/sekolah</li>
          <li>✅ Peluang income dari industri finansial & edukasi</li>
          <li>✅ Komunitas anak muda ambisius & berorientasi goal</li>
        </ul>
      </section>

      <section className="max-w-3xl mx-auto bg-green-50 rounded-2xl p-6 md:p-10 mb-8">
        <h2 className="text-2xl font-semibold mb-4">Siapa yang Cocok?</h2>
        <p className="mb-4 text-gray-700">Kita cari kamu yang:</p>
        <ul className="space-y-2 text-gray-700">
          <li>🎯 Punya semangat belajar dan pengen berkembang</li>
          <li>📱 Aktif di media sosial dan senang komunikasi</li>
          <li>💡 Punya mimpi besar dan siap kerja bareng tim</li>
        </ul>
      </section>

      <section className="max-w-3xl mx-auto bg-white shadow-lg rounded-2xl p-6 md:p-10">
        <h2 className="text-2xl font-bold mb-4 text-center">Tertarik? Isi Form Ini 👇</h2>
        <p className="mb-6 text-gray-600 text-center">
          Kamu nggak harus expert, yang penting niat dan mindset berkembang.
        </p>
        <form className="space-y-6" onSubmit={handleSubmit}>
          <div>
            <label className="block mb-1 font-medium">Nama Lengkap</label>
            <input name="nama" type="text" value={form.nama} onChange={handleChange} className="w-full border rounded-lg px-4 py-2" placeholder="Contoh: Dimas Pratama" />
            {error.nama && <p className="text-red-500 text-sm mt-1">{error.nama}</p>}
          </div>

          <div>
            <label className="block mb-1 font-medium">Usia</label>
            <input name="usia" type="number" value={form.usia} onChange={handleChange} className="w-full border rounded-lg px-4 py-2" placeholder="Contoh: 17" />
            {error.usia && <p className="text-red-500 text-sm mt-1">{error.usia}</p>}
          </div>

          <div>
            <label className="block mb-1 font-medium">Asal Kota</label>
            <input name="kota" type="text" value={form.kota} onChange={handleChange} className="w-full border rounded-lg px-4 py-2" placeholder="Contoh: Jakarta / Bekasi" />
            {error.kota && <p className="text-red-500 text-sm mt-1">{error.kota}</p>}
          </div>

          <div>
            <label className="block mb-1 font-medium">Instagram</label>
            <input name="instagram" type="text" value={form.instagram} onChange={handleChange} className="w-full border rounded-lg px-4 py-2" placeholder="@username" />
          </div>

          <div>
            <label className="block mb-1 font-medium">Nomor WhatsApp</label>
            <input name="whatsapp" type="text" value={form.whatsapp} onChange={handleChange} className="w-full border rounded-lg px-4 py-2" placeholder="08xxxxxx" />
            {error.whatsapp && <p className="text-red-500 text-sm mt-1">{error.whatsapp}</p>}
          </div>

          <div>
            <label className="block mb-1 font-medium">Kenapa kamu tertarik join?</label>
            <textarea name="motivasi" value={form.motivasi} onChange={handleChange} className="w-full border rounded-lg px-4 py-2" rows="4" placeholder="Ceritain sedikit tentang motivasi kamu..."></textarea>
            {error.motivasi && <p className="text-red-500 text-sm mt-1">{error.motivasi}</p>}
          </div>

          <div className="text-center">
            <button type="submit" className="bg-green-600 text-white px-6 py-3 rounded-full text-lg hover:bg-green-700 transition">
              Kirim Formulir
            </button>
          </div>
        </form>
      </section>

      <footer className="text-center mt-12 text-gray-500 text-sm">
        © 2025 Made by Marvel | Financial Growth Partner
      </footer>
    </div>
  );
}
