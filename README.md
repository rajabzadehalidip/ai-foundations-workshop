# AI Foundations Workshop

Standalone workshop materials for Ali Rajabzadeh, Researcher at Sharif Center for AI Strategy and Transformation.

## Files

- `index.html` — standalone presentation; open locally or host with GitHub Pages.
- `competition-openrouter-embeddings-colab.ipynb` — Google Colab activity using OpenRouter embeddings, PCA, classification, and review queues.
- `competition-corpus.csv` — classroom dataset with public-source links and paraphrased competition-policy material.
- `competition-corpus-fa.csv` — Persian classroom dataset with natural, paraphrased Iranian digital-market examples.
- `competition-hands-on-guide.md` — facilitator instructions and discussion questions.
- `telegram_policy_radar_4topics_openrouter_colab.ipynb` — API-based Persian embeddings lab: four-topic classification, PCA map, semantic search, and human-review queue.
- `telegram_policy_radar_4topics_fa.csv` — cleaned, unlabeled 160-post Persian classroom dataset for that lab.
- `telegram_policy_radar_4topics_openrouter_guide.md` — Persian facilitator guide for the API-based lab.

## Share the presentation

Open `index.html` in a browser. Press `E` to edit text, upload the presenter photo, add or duplicate slides, and download an edited copy.

## Colab

Upload `competition-corpus.csv` into the notebook when prompted. The notebook requires an OpenRouter API key with a small usage limit. Do not upload confidential material or commit API keys.

### Telegram Policy Radar (API-based)

Upload `telegram_policy_radar_4topics_fa.csv` into `telegram_policy_radar_4topics_openrouter_colab.ipynb`. Each student enters their own OpenRouter key through a hidden Colab prompt; the key is never stored in the notebook. The workflow calls OpenRouter's embeddings API using `openai/text-embedding-3-small`, then explores four BANA-relevant themes: regulation, AI and data, competition and digital platforms, and telecom infrastructure. The dataset has no gold-standard labels; it is intended for replication, interpretation, and human review.

## GitHub Pages

After pushing this folder to a GitHub repository, enable Pages under **Settings → Pages → Deploy from branch → main → /(root)**. The presentation will be available at the repository's GitHub Pages URL.
