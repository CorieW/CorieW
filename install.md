# Fireconduit

## 1) Install (one command)

1. Click **Open in Google Cloud Shell** above.
2. Make sure you’re on the right project:

   ```bash
   gcloud config set project YOUR_PROJECT_ID
   ```
3. Run:

   ```bash
   bash scripts/setup.sh
   ```

That’s it—Fireconduit will enable required APIs and set up backfill + streaming from Firestore to BigQuery.

---

## Optional settings (skip if defaults are fine)

You can override defaults via env vars:

```bash
export REGION="us-central1"
export FIRESTORE_DATABASE="(default)"
export BQ_DATASET="fireconduit"
export COLLECTIONS='["users","orders"]'   # initial backfill
bash scripts/setup.sh
```

Or flags:

```bash
bash scripts/setup.sh \
  --project YOUR_PROJECT_ID \
  --region us-central1 \
  --firestore-database "(default)" \
  --bq-dataset fireconduit \
  --collections '["users","orders"]'
```

---

## Verify

* **BigQuery:** look for tables in `fireconduit` (e.g., `fs_users`, `fs_orders`).
* **Logs:** check Cloud Logging for Fireconduit job status.

---

## Uninstall

```bash
bash scripts/setup.sh --destroy
```

(Data already written to BigQuery stays unless you remove it.)

---

## Troubleshooting

* Set project: `gcloud config set project YOUR_PROJECT_ID`
* Re-run setup if an API wasn’t enabled.
* Missing permission? Ask your admin for the roles shown in the error (e.g., BigQuery Admin).

---

**Ready to go.** One button, one command. If you share your repo URL and preferred defaults, I can swap the placeholders for you.
