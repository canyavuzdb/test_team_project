# Vanilla App Template

Bu proje Vite ile oluşturulmuştur. Tanışmak ve yapılandırmak için
ek özellikler [belgelere bakın](https://vitejs.dev/).

## Şablon kullanarak bir depo oluşturma

Kendi deponuzu oluşturmak için bu GoIT deposunu şablon olarak kullanın
projenizin deposu. Bunu yapmak için `«Use this template»` ve
seçeneğini seçin `«Create a new repository»`, resimde gösterildiği gibi.

![Creating repo from a template step 1](./assets/template-step-1.png)

Bir sonraki adım sizi yeni bir depo oluşturma sayfasına götürür. Doldurun
alanına tıklayın, deponun herkese açık olduğundan emin olun ve ardından
düğme `«Create repository from template»`.

![Creating repo from a template step 2](./assets/template-step-2.png)

Depo oluşturulduktan sonra, ayarlara gitmeniz gerekir
sekmesine oluşturulan deponun `Settings` > `Actions` > `General` görüntü üzerinde 
gösterildiği gibi.

![Settings GitHub Actions permissions step 1](./assets/gh-actions-perm-1.png)

Sayfanın en sonuna kaydırın, içinde `«Workflow permissions»` 
bir seçenek seçin `«Read and write permissions»` ve onay kutusunu işaretleyin.
Bu, proje dağıtım sürecini otomatikleştirmek için gereklidir.

![Settings GitHub Actions permissions step 2](./assets/gh-actions-perm-2.png)

Artık şablon deposunun dosya ve klasör yapısına sahip kişisel bir proje deponuz var. 
Daha sonra diğer kişisel depolarda yaptığınız gibi çalışın, bilgisayarınıza klonlayın,
kod yazın, taahhütlerde bulunun ve bunları GitHub'a gönderin.

## İş için hazırlanma

1. Bilgisayarınızda Node.js'in LTS sürümünün yüklü olduğundan emin olun. 
Gerekirse [İndirin ve yükleyin](https://nodejs.org/en/)
2. Terminalde temel proje bağımlılıklarını şu komutla ayarlayın `npm install`.
3. Terminalde şu komutu çalıştırarak geliştirme modunu başlatın `npm run dev`.
4. Tarayıcınızda aşağıdaki adrese gidin
[http://localhost:5173](http://localhost:5173). Proje dosyalarında yaptığınız
değişiklikleri kaydettikten sonra bu sayfa otomatik olarak yeniden yüklenecektir.

## Dosyalar ve klasörler

- Sayfa bileşenlerinin biçimlendirme dosyaları `rc/partials` klasöründe bulunmalı ve 
`index.html` dosyasına aktarılmalıdır. Örneğin, başlık işaretlemesini içeren 
`header.html` dosyası `partials` klasöründe oluşturulur ve `index.html` dosyasına aktarılır.
- Stil dosyaları `rc/css` klasöründe bulunmalı ve sayfaların HTML dosyalarına aktarılmalıdır. 
Örneğin, `index.html` için stil dosyası `index.css` olarak adlandırılır.
- Resimleri `src/img` klasörüne ekleyin. Oluşturucu bunları optimize edecektir, 
ancak yalnızca projenin üretim sürümünü dağıttığınızda. 
Tüm bunlar bilgisayarınıza yük olmaması için bulutta gerçekleşir,
çünkü zayıf bilgisayarlarda uzun zaman alabilir.

## Dağıtım

Projenin üretim sürümü, `main` dalı güncellendiğinde otomatik olarak oluşturulacak ve 
`gh-pages` dalında GitHub Pages'a dağıtılacaktır. Örneğin, doğrudan bir push veya 
kabul edilen bir pool-request sonrasında. Bunu yapmak için, `build` komutu için `package.json` dosyasındaki 
`--base=/<REPO>/` bayrağının değerini değiştirmeniz, `<REPO>` yerine 
deponuzun adını yazmanız ve değişiklikleri GitHub'a göndermeniz gerekir.

```json
"build": "vite build --base=/<REPO>/",
```

Ardından, GitHub depo ayarlarına gitmeniz (`Ayarlar > `Sayfalar') ve otomatik olarak yapılmadıysa, 
dosyaların üretim sürümünün `gh-pages' dalının `/root' klasöründen dağıtımını ayarlamanız gerekir.

![GitHub Pages settings](./assets/repo-settings.png)

### Depoziter statüsü

Edge commit dağıtımının durumu, tanımlayıcısının yanındaki simge ile gösterilir.

- **Sarı** - proje inşa ediliyor ve konuşlandırılıyor.
- **Yeşil**, dağıtımın başarılı olduğu anlamına gelir.
- **Kırmızı** - bağlama, oluşturma veya dağıtma sırasında bir hata oluştu.

Durum hakkında daha ayrıntılı bilgi, simgeye tıklayarak ve açılan penceredeki
`Detaylar` bağlantısını takip ederek görüntülenebilir.

![Deployment status](./assets/deploy-status.png)

### Canlı sayfa

Bir süre sonra, genellikle birkaç dakika, canlı sayfa depo ayarlarındaki 
`Ayarlar` > `Sayfalar` sekmesinde belirtilen adresten görüntülenebilir. 
Örneğin, bu depo için canlı sürümün bağlantısı şöyledir

[https://goitacademy.github.io/vanilla-app-template/](https://goitacademy.github.io/vanilla-app-template/).

Boş bir sayfa görürseniz, `Console` sekmesinde projenin CSS ve JS dosyalarının 
yanlış yollarıyla ilgili herhangi bir hata olmadığından emin olun (**404**). 
Büyük olasılıkla, `package.json' dosyasında `build' komutu için `--base' bayrağının yanlış bir değerine sahipsiniz.

## Nasıl çalışır

![How it works](./assets/how-it-works.png)

1. GitHub deposunun `main` dalına yapılan her push işleminden sonra, 
`.github/workflows/deploy.yml` dosyasından özel bir betik (GitHub Action) çalıştırılır.
2. Tüm depo dosyaları sunucuya kopyalanır, 
burada proje başlatılır ve dağıtımdan önce bağlama ve oluşturma işlemlerinden geçirilir.
3. Tüm adımlar başarılı olduysa, proje dosyalarının birleştirilmiş üretim sürümü `gh-pages` dalına gönderilir. 
Aksi takdirde, kod yürütme günlüğü sorunun ne olduğunu gösterecektir.