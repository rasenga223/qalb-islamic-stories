# 📖 Qalb Stories Repository

This repository stores story metadata for the **Qalb Islamic App** in a simple JSON format.
The goal is to provide **authentic, multilingual Islamic stories**.

---

## 📂 Repository Structure

```
qalb-stories/
│
├── stories.json     # Main JSON file with all stories
├── images/          # (Optional) Folder for hosting images locally if needed
└── README.md
```

---

## 📝 Story JSON Format

Each story entry is an object with the following fields:

| Field         | Type   | Description                                                                |
| ------------- | ------ | -------------------------------------------------------------------------- |
| `id`          | Number | Unique story ID                                                            |
| `title`       | String | Name of the story                                                          |
| `languages`   | Object | Key-value pairs of language codes and their story links (audio/text/video) |
| `image`       | String | URL to a thumbnail image for the story                                     |
| `description` | String | Short summary of the story                                                 |
| `source`      | String | Reference to the original source (e.g., book, hadith collection, etc.)     |

---

## 📄 Example

```json
[
  {
    "id": 1,
    "title": "Prophet Adam (AS)",
    "languages": {
      "english": "https://soundcloud.com/safarpublications/adam-english",
      "arabic": "https://soundcloud.com/safarpublications/adam-arabic",
      "french": "https://soundcloud.com/safarpublications/adam-french"
    },
    "image": "https://example.com/images/adam.jpg",
    "description": "The first human created by Allah, father of mankind.",
    "source": "Qasas al-Anbiya by Ibn Kathir"
  }
]
```

---

## 🔗 Raw JSON URL

You can fetch the `stories.json` file directly from GitHub’s raw file link:

```
https://raw.githubusercontent.com/YOUR_USERNAME/qalb-stories/main/stories.json
```

---

## 🚀 How to Use in an App

Example in **React Native / JavaScript**:

```javascript
const fetchStories = async () => {
  const url = "https://raw.githubusercontent.com/YOUR_USERNAME/qalb-stories/main/stories.json";
  const res = await fetch(url);
  const data = await res.json();
  return data;
};
```

Optional: Cache stories for offline use:

```javascript
import AsyncStorage from '@react-native-async-storage/async-storage';

const getStories = async () => {
  try {
    const res = await fetch("https://raw.githubusercontent.com/YOUR_USERNAME/qalb-stories/main/stories.json");
    const stories = await res.json();
    await AsyncStorage.setItem('stories', JSON.stringify(stories));
    return stories;
  } catch (error) {
    const cached = await AsyncStorage.getItem('stories');
    return cached ? JSON.parse(cached) : [];
  }
};
```

---

## 🤝 Contributing

We welcome contributions from the community to expand this library of authentic Islamic stories.

### 📌 Contribution Guidelines

1. **Authenticity First**

   * Only include stories from **authentic sources** such as the Qur’an, Sahih hadith collections, and reliable Islamic history books (e.g., *Qasas al-Anbiya* by Ibn Kathir).
   * Always provide a `source` reference in the story entry.

2. **Format Consistency**

   * Follow the JSON structure exactly.
   * Ensure all fields are present: `id`, `title`, `languages`, `image`, `description`, `source`.

3. **Language Links**

   * Use public, direct URLs for the `languages` links (e.g., SoundCloud, YouTube, MP3 file links).
   * If a language version is unavailable, omit that key from the `languages` object.

4. **Images**

   * Use URLs to images hosted on public CDNs or trusted hosting platforms.
   * Avoid copyrighted or watermarked images unless permission is granted.

---

### 🛠 Steps to Add a Story

1. **Fork** this repository.
2. Open the `stories.json` file.
3. Add your new story object at the end of the array.
4. Increment the `id` number.
5. Commit your changes with a meaningful message.
6. Open a **Pull Request (PR)** explaining your story addition and source.

---

### ✅ Example Contribution

```json
{
  "id": 2,
  "title": "Prophet Nuh (AS)",
  "languages": {
    "english": "https://soundcloud.com/safarpublications/nuh-english"
  },
  "image": "https://example.com/images/nuh.jpg",
  "description": "The Prophet who built the Ark and called his people to worship Allah.",
  "source": "Qasas al-Anbiya by Ibn Kathir"
}
```

---

## 📜 License

This repository is provided under the **MIT License**.
You may use and distribute the data freely, provided you **credit the source** and ensure **authenticity**.

---

## 📧 Contact

If you have any questions or suggestions, open an issue or contact us at https://qalbapp.com.
