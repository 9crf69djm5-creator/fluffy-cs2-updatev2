# Updates: use your own server (no GitHub)

Use the **regular** update flow:

1. In the **project root**, run **BUILD_UPDATES.bat**.
2. Upload the contents of the **upload_this** folder to your own server (any host).
3. In the same folder as the Loader, create **update_config.txt** with one line:
   ```
   BaseUrl=https://yoursite.com/yourpath/
   ```
   (Your URL must end with `/` and serve **version.txt** and **CS2 External.exe**.)

The loader will then check that URL and update the cheat when you release a new build.
