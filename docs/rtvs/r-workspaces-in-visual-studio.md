---
title: R çalışma alanları
description: R kodunun çalışma alanlarını kullanarak R kodunun nerede Visual Studio.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 4d50f0a6ddda29378413463b339faf28f9294de4
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750785"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Çalışma alanlarıyla R kodunun nerede çalıştırı olduğunu denetleme

Visual Studio için R Araçları (RTVS) çalışma alanı, R oturumunun nerede çalıştırıldığında hem yerel hem de uzak bilgisayarlarda gerçekleşecek şekilde yapılandırmaya olanak sağlar. Amaç, daha güçlü olabilecek bulut tabanlı bilgisayarlardan faydalanma olanağı sağlayan karşılaştırılabilir bir kullanıcı deneyimiyle çalışma olanağı elde etmektir.

Çalışma Alanları penceresini **açmak için** **R** Araçları'Windows Çalışma  >  **Alanları**  >  **komutunu** kullanın veya **Ctrl** + **9 tuşlarına basın.**

![Visual Studio için R Araçları'de çalışma alanları penceresi (VS2017)](media/workspaces-window.png)

Bu pencerede yeşil onay işareti RTVS'nin bağlı olduğu etkin çalışma alanını gösterir. Mavi ok seçmek etkin çalışma alanını ayarlar. Her çalışma alanının sağ yanındaki ayarlar (dişli) simgesi, çalışma alanının adını, konumunu ve komut satırı bağımsız değişkenlerini değiştirmenizi sağlar. Kırmızı X, el ile eklenen çalışma alanını kaldırır.

## <a name="save-and-reset-a-workspace"></a>Çalışma alanını kaydetme ve sıfırlama

Varsayılan olarak RTVS, bir projeyi kapatıp yeniden açarak çalışma alanı durumunu kaydetmez. Ancak, bu davranışı Çalışma alanı seçenekleri aracılığıyla [değiştirebilirsiniz.](options-for-r-tools-in-visual-studio.md#workspace)

Etkileşimli **pencerede R Araçları** Oturum Sıfırlama komutu ve araç çubuğu sıfırlama düğmesi de herhangi bir zamanda çalışma alanı durumunu  >    >   sıfırlar. Uzak çalışma alanları ile sıfırlama, uzak sunucuya ilk kez bağlanırken oluşturulan kullanıcı profilini siler ve burada biriken tüm dosyaları etkili bir şekilde siler.

## <a name="local-workspaces"></a>Yerel çalışma alanları

Yerel çalışma alanları listesi, bilgisayarınızda yüklü olan tüm R yorumlayıcılarını görüntüler.

Bu Visual Studio, kayıt defteri anahtarına bakarak yüklü olan tüm R sürümlerini otomatik olarak **HKEY_LOCAL_MACHINE\Software\R-Core\\** çalışır. Bu denetim yalnızca başlangıçta olduğundan, yeni bir R yorumlayıcı Visual Studio yeniden başlatmanız gerekir.

RTVS, standart olmayan bir şekilde yüklenmiş olan bir R yorumlayıcıyı algılamayabilirsiniz (örneğin, dosyaları bir yükleyiciyi çalıştırma yerine bir klasöre kopyalayıp kopyalamanız gerekir). Bu durumda, aşağıdaki gibi el ile yeni bir yerel R Çalışma Alanı oluşturun:

1. Çalışma **Alanları** penceresinde Ekle düğmesini seçin.
1. Yeni Çalışma Alanı için bir ad girin.
1. Yorumlayıcı ile birlikte bin klasörünü içeren R kök  klasörünün yolunu ve RTVS başlatıldığında yorumlayıcıya geçiş için isteğe bağlı komut satırı bağımsız değişkenlerini girin.
1. İşiniz bittiğinde **Kaydet**’i seçin.

![Yeni çalışma alanı ekleme](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Uzak çalışma alanları

Uzak çalışma alanları, uzak bir bilgisayarda R oturumuna bağlanmanıza olanak sağlar. (Bir [bilgisayarı bu amaçla yapılandırma hakkında](setting-up-remote-r-workspaces.md) bilgi için bkz. Uzak çalışma alanlarını ayarlama.)

Visual Studio, uzak çalışma alanlarını otomatik olarak algılamaz, bu nedenle  önceki bölümde açıklandığı gibi Çalışma Alanları penceresindeki Ekle düğmesini kullanarak el ile eklemeniz gerekir. Bu durumda, yerel yol yerine uzak bilgisayarın URI'lerini girin.

> [!Important]
> Uzak çalışma alanları, uzak bilgisayarla iletişimin gizliliğini ve bütünlüğünü sağlamak için *HTTPS* protokolünü kullanması gereken bir URI ile tanımlanır. Visual Studio HTTPS'yi desteklemez uzak bir bilgisayara bağlanamaz.

> [!Note]
> Uzak çalışma alanları etkin bir şekilde önizlemededir. Gelecek sürümlerden biri için dosya eşitleme sorununu daha iyi bir şekilde uygulamaya çalışıyoruz ve fikirlerinizi ve geri bildirimlerinizi bekliyoruz.

## <a name="remote-workspace-logon"></a>Uzak Çalışma Alanı Oturum Açma

Uzak çalışma alanında oturum açmanız için kullanıcı adı ve parola kullansanız iyi olur.

### <a name="logon-to-windows-workspace"></a>Çalışma alanında Windows açma

Uzak makineniz etki alanı hesabını kullanmak üzere ayar kullanıyorsa, uzak bir çalışma alanına erişmek için etki alanı oturum açma adını kullanabilirsiniz. Oturum açmadıysanız, uzak makinede bir `machine-name\username` makine hesabı kullanarak oturum a açabilirsiniz.

### <a name="logon-to-linux-workspace"></a>Linux çalışma alanında oturum açma

Linux hesabında oturum açma için biçimini `<<unix>>\username` kullanın. Örneğin, adına sahip bir hesabınız varsa `ruser` kullanıcı adını olarak yazmanız `<<unix>>\ruser` gerekir.

## <a name="switch-between-workspaces"></a>Çalışma alanları arasında geçiş

RTVS aynı anda yalnızca tek bir çalışma alanına bağımlıdır. Bağlı çalışma alanı, Çalışma Alanları penceresinde küçük bir yeşil onay işaretiyle gösterilir. RtVS varsayılan olarak önceki oturumda son açık yerel çalışma alanına bağlar.

Etkin çalışma alanını değiştirmek için, istenen çalışma alanının yanındaki mavi oku seçin. Bunu yapmak oturum kaydetmenizi, geçerli çalışma alanını sonlandırmanızı ve ardından yeni çalışma alanına geçmenizi sağlar.

> [!Tip]
> Kaydetme istemini devre dışı bırakmak için **R Araçları** Seçenekleri komutunu seçin ve çalışma alanları seçeneğini olarak değiştirmeden önce Onayı  >   göster **iletişim** kutusunu `No` ayarlayın. Bkz. [Çalışma alanı seçenekleri.](options-for-r-tools-in-visual-studio.md#workspace)

Kaldırdığınız yerel çalışma alanına veya kullanılamayan bir uzak çalışma alanına geçmeyi denerse RTVS herhangi bir çalışma alanına bağlı olmayabilir. Sonuç olarak, etkileşimli pencereye kod girerken veya aksi takdirde kod çalıştırmayı deneyebilirsiniz:

![RTVS'ye bağlı çalışma alanı yok hatası](media/workspaces-disconnected-interactive-window.png)

Bunu düzeltmek için Çalışma Alanları penceresinde başka bir çalışma alanına geçiş oluşturun. Kullanılabilir çalışma alanı yoksa bir R yorumlayıcı yüklemeniz gerekir. Ayrıca, çalışırken Visual Studio bir yorumlayıcı yükledikten sonra yeniden başlatmayı Visual Studio denemesi.

### <a name="switch-to-a-remote-workspace"></a>Uzak çalışma alanına geçme

RTVS, uzak bir çalışma alanına ilk kez bağlanıyorsanız kimlik bilgilerini girmenizi, ardından bu kimlik bilgilerini sonraki oturumlar için önbelleğe alır (güvenli kimlik Windows Kimlik Bilgileri Kasası kullanarak). Uzak sunucuyla iletişim daha sonra HTTPS üzerinden güvenli bir şekilde yapılır (bu gereklidir).

Sunucunun yapılandırmasına bağlı olarak, bağlanırken "Uzak R Hizmetleri tarafından sunulan güvenlik sertifikası, gerçekten makineye (ad) bağlanıyor olduğunu kanıtlamamıza izin vermiyor. "

![Uzak çalışma alanına bağlanırken otomatik olarak imzalanan sertifika uyarısı](media/workspaces-remote-self-signed-certificate-warning.png)

Sertifika, bağlanmaya çalıştığınız bilgisayar tarafından RTVS'ye sunulan bir belgedir. Sertifika, o bilgisayarın URI'sını tanımlayan bir alan içerir. RTVS, sertifikada URI ile bilgisayara bağlanmak için kullanılan URI arasında bir eşleşme olmadığını algılayan ve sunucunun güvenliğinin tehlikeye atılmış olduğunu belirten bir uyarı görüntülenir.

Ancak, güvenilir bir sağlayıcıdan *bir* sertifika kullanmak yerine uzak bilgisayarda HTTPS'yi etkinleştirmek için otomatik olarak imzalanan bir sertifika kullanılıyorsa da bu uyarı görüntülenir. Daha fazla bilgi için [bkz. Uzak çalışma alanlarını ayarlama.](setting-up-remote-r-workspaces.md)

## <a name="directories-on-local-and-remote-computers"></a>Yerel ve uzak bilgisayarlarda dizinler

Varsayılan olarak, yerel çalışma alanında yeni bir R yorumlayıcıyı başlatarak geçerli çalışma dizininiz *%userprofile%\Documents olur.* **R** Araçları Çalışma Dizini komutlarını kullanarak veya çalışma dizininde bir projeye sağ tıklar ve Çalışma Dizinini Burada Ayarla gibi komutları Visual Studio Çözüm Gezgini istediğiniz zaman  >   **dizini değiştirebilirsiniz.**

Uzak bir bilgisayara ilk kez bağlanıyorsanız RTVS, kimlik bilgilerinize göre otomatik olarak bir kullanıcı profili oluşturur ve çalışma dizini bu profil altındaki *Belgeler* klasörüne ayarlanır. Bu klasör, aynı kimlik bilgilerini kullanan sonraki tüm uzak oturumlar için kullanılır.

Sonuç olarak, kodunuzun çalıştır olduğu konum yerel ve uzak çalışma alanları arasında farklılık gösterebilir. Kodunda, kodunuzun çalışma alanları arasında taşınabilir olması için her zaman veri dosyalarına göreli yollar kullanın.

Ayrıca, uzak çalışma alanlarıyla çalışma dizininde yer alan tüm dosyaların aynı kullanıcı profili için oturumlar arasında yerinde kalır. Daha önce belirtildiği gibi, uzak bir çalışma alanı kullanırken **R Araçları** Oturum Sıfırlama komutunu (veya etkileşimli pencerede sıfırla düğmesini) kullanarak bu  >    >   dosyaları silebilirsiniz. Bu komut yeniden bağlandığınızda yeniden oluşturulan kullanıcı profilini sunucudan siler.

## <a name="copy-project-files-to-remote-workspaces"></a>Proje dosyalarını uzak çalışma alanlara kopyalama

Uzak çalışma alanında R Visual Studio çalışırken, uzak çalışma alanı kullanırken bile yerel bilgisayarda her zaman en son proje dosyaları olur. Başka bir ifadeyle bir projeyi Visual Studio (genellikle bu projeyi içeren bir çözümün açılması anlamına gelir) RTVS, projenin içeriğinin yerel bilgisayarda olduğunu varsayıyor. Uzak çalışma alanı aslında proje dosyaları ve koddan alınan çıkışlar için geçici bir konaktır. Bu, örneğin, etkileşimli pencerede kullanarak bir dosya yüklerken, bu dosyanın, sizin sağ istediğiniz yolda uzak bilgisayarda olması veya uzak R yorumlayıcının geçerli çalışma dizininde olması (işleviyle ayarlanmış) olması anlamına `source` `setwd()` gelir.

Dosyalar aşağıdaki gibi uzak sunucuya kopyalanır:

- Etkileşimli pencere aracılığıyla dosyalarla uzaktan çalışmak için önce dosyalarda bu dosyalara (veya projeye) sağ tıklayıp Kaynak Seçildi'yi Çözüm Gezgini el **ile kopyalamanız gerekir.** Tek tek dosyalar için sunucu üzerinde çalışma dizinine kopyalanır; RTVS, bir projeyi kopyalayıp proje için bir klasör oluşturur.

- Ayrıca, dosyalarda öğesini ve ardından Kaynak Seçilen Çözüm Gezgini'yi seçerek **dosyaları kopyaabilirsiniz.** Bu eylem bunları etkileşimli pencereye yükler ve orada çalıştırır. Oturum uzak bir bilgisayara bağlı ise, dosyalar önce bu bilgisayara kopyalanır.

- RTVS bir uzak çalışma alanına bağlı olduğunda **ve F5** tuşuna basıyorsanız Hata AyıklamaYı Başlat'ı seçin veya kodunuzu çalıştırmaya başka bir şekilde başlarsanız RTVS varsayılan olarak projenin dosyasını otomatik olarak uzak çalışma alanına kopyalar (bu davranışın nasıl kontrol etmek için aşağıya   >  bakın).

- Sunucuda zaten mevcut olan dosyaların üzerine yazılır.

> [!Note]
> RTVS tüm R işlev çağrılarını güvenilir bir şekilde araya alamayasa da etkileşimli pencere içindeki veya gibi çağırma işlevleri (Shiny uygulamaları için) dosyaları uzak çalışma `source()` `runApp()` alanına kopyalamaz. 

[Project,](r-projects-in-visual-studio.md#project-properties) rtvs'nin bir proje çalıştırıldık zaman dosyaları kopyaip kopyalaymayacaklarını ve tam olarak hangi dosyaların kopyalandırıp kopyalanmayacaklarını kontrol etmek için kullanılır. Bu sayfayı açmak için Project (ad) Özellikler menü komutunu seçin veya Çözüm Gezgini'de  >   projeye sağ tıklayın ve Özellikler'i **seçin.**

![Project özellikleri dosya aktarımı ayarlarıyla sekmeyi çalıştırma](media/workspaces-remote-file-transfer-filter-settings.png)

Burada Transfer **files on run özelliği** RTVS'nin proje dosyalarını otomatik olarak kopyaip kopyalay olmadığını belirler. Aktar **aktarılan dosyalar değeri,** tam olarak hangi dosyaların aktarıldıklarını filtreler. Varsayılan değer yalnızca *kopyalamaktır. R*, *. Rmd*, *.sql*, *.md* ve *.cpp* dosyaları. Bu davranış, büyük veri dosyalarını istemeden her çalıştırmada sunucuya kopyalamayı önler.

## <a name="copy-files-from-a-remote-workspace"></a>Uzak çalışma alanında yer alan dosyaları kopyalama

R betiğiniz sunucuda dosya üretirse, işlevini kullanarak bu dosyaları istemciye geri `rtvs::fetch_file` kopyaabilirsiniz. Bu işlev, bilgisayarınıza kopyalamak istediğiniz dosyanın uzak yolunu ve isteğe bağlı olarak bilgisayarınızda hedef yolu kabul eder. Bir yol belirtmezseniz, dosya *%userprofile%\Downloads klasörünüze kopyalanır.*
