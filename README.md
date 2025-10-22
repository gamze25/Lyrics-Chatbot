# Lyrics-Chatbot
# Şarkı Bulma Chatbotu

Günlük hayatta çok sık aklıma rastgele şarkı sözleri geliyor ve bunların hangi şarkıya ait olduğunu kolaylıkla hatırlayamıyorum. Bu sorunu benim gibi birçok kişinin de yaşadığını biliyorum bu yüzden projemde bu soruna yer vermek istedim. Oluşturduğum chatbot'a herhangi bir şarkı sözü girildiğinde yanıt olarak yüklediğim veri setinden yararlanarak o sözlerin hangi şarkıya ait olduğunu ve sanatçının ismini bize veriyor. Veri setimi hugging face üzerinden araştırıp buldum. 

---

## 🧠 RAG Pipeline Adımlarım

1. **Veri Toplama:**  
   Hugging Face’ten alınan `SpartanCinder/song-lyrics-artist-classifier` veri seti kullanılır.  
   (13.596 şarkı sözü içerir 🎵)

2. **Belge Dönüştürme:**  
   Her satır `Document` formatına çevrilir (`lyrics`, `artist`, `song`).

3. **Embedding Oluşturma:**  
   `sentence-transformers/all-mpnet-base-v2` modeli ile semantik vektörler oluşturulur.

4. **Vektör Depolama:**  
   Tüm embeddingler **ChromaDB** veritabanında saklanır.

5. **Benzerlik Arama (Retriever):**  
   Girilen şarkı sözüne en çok benzeyen 3 şarkı getirtilir.

6. **Cevap Üretimi:**  
   Google **Gemini 2.0 Flash** modeli kullanılarak Türkçe, samimi ve kısa bir yanıt üretilir.

---

## Collab dosya linkim:
https://colab.research.google.com/drive/1pliN2AxVnploPGQVfvNJAtwIFxchLanp?usp=sharing

 **Kullanım:**
1. “Runtime > Run all” diyerek tüm hücreleri çalıştır.  
2. En alttaki hücre Gradio arayüzünü başlatır.  
3. Aşağıdaki gibi bir link göreceksin:  

4. Bu bağlantıya tıklayarak **chatbot arayüzünü** açabilirsin.  
5. Arayüzde bir şarkı sözü gir → sistem sana **en benzer 3 şarkıyı** getirir.  

---

## Kullanılan Teknolojiler  

| Alan | Teknoloji |
|------|------------|
| LLM | Google Gemini 2.0 Flash |
| Framework | LangChain |
| Embedding | Hugging Face (all-mpnet-base-v2) |
| Vektör Veritabanı | ChromaDB |
| Arayüz | Gradio |
| Geliştirme Ortamı | Google Colab |
| Veri Seti | SpartanCinder/song-lyrics-artist-classifier |

---

## Proje Yapısı  
Lyrics-Chatbot/
├── lyricschatbot.ipynb # Ana Colab not defteri
├── requirements.txt # Kütüphaneler listesi
├── README.md # Proje açıklaması
