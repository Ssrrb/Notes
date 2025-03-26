For cloud storage, install the ClearML package for your cloud storage type:
- Google Storage - `pip install clearml[gs]`


---

### ✅ **1. Use `StorageManager` for Managing Data**
- **Purpose:** Download, upload, and cache files directly from your code.
- **Action:** Use ClearML’s `StorageManager` class in your Python scripts.

---

### ✅ **2. Enable Path Substitution**
- **Use Case:** When datasets are stored in different locations for different users.
- **Action:**
  1. Open `clearml.conf`.
  2. Add your mappings under `sdk > storage > path_substitution` like this:
     ```yaml
     sdk {
         storage {
             path_substitution = [
                 {
                     registered_prefix = "s3://bucket/research"
                     local_prefix = "file:///mnt/shared/bucket/research"
                 },
                 {
                     registered_prefix = "file:///mnt/shared/folder/"
                     local_prefix = "file:///home/user/shared/folder"
                 }
             ]
         }
     }
     ```

---

### ✅ **3. Configure Caching**
- **Purpose:** Prevent duplicate downloads and speed up data access.
- **Action:**
  1. In `clearml.conf`, define the cache base directory:
     ```yaml
     sdk {
         storage {
             cache {
                 default_base_dir: "~/.clearml/cache"
             }
         }
     }
     ```

---

### ✅ **4. Enable Direct Access (Optional)**
- **Use Case:** For local/NFS filesystems where data shouldn’t be copied to cache.
- **Action:**
  1. In `clearml.conf`, add a `direct_access` block:
     ```yaml
     sdk {
         storage {
             direct_access: [
                 { url: "file://*" }  # Automatically use files directly without downloading
             ]
         }
     }
     ```

---

