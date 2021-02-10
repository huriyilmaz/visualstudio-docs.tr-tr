---
title: R çalışma alanları
description: R kodunun, Visual Studio 'da çalışma alanlarını kullanarak nerede çalıştığını denetleme.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3627a8944941fc77bb9b19fe3dd0a1549f41892a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961592"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>R kodunun çalışma alanlarıyla çalıştığı yeri denetleme

Visual Studio için R Araçları (RTVS) içindeki bir çalışma alanı, bir R oturumunun nerede çalıştığını, hem yerel hem de uzak bilgisayarlarda meydana gelen bir şekilde yapılandırmanıza olanak tanır. Amaç, potansiyel olarak daha güçlü bulut tabanlı bilgisayarlardan yararlanmanızı sağlayan, karşılaştırılabilir bir kullanıcı deneyimiyle birlikte çalışmanıza olanak sağlamaktır.

**Çalışma alanları** penceresini açmak için **R araçları**  >  **Windows**  >  **çalışma alanları** komutunu kullanın veya **CTRL** + **9**' a basın.

![Visual Studio için R Araçları çalışma alanları penceresi (VS2017)](media/workspaces-window.png)

Bu pencerede, yeşil onay işareti RTVS 'nin bağlandığı etkin çalışma alanını gösterir. Mavi ok seçilmesi etkin çalışma alanını ayarlar. Her bir çalışma alanının sağ tarafındaki ayarlar (dişli) simgesi, adını, konumunu ve komut satırı bağımsız değişkenlerini değiştirmenize olanak sağlar. Kırmızı X El ile eklenen bir çalışma alanını kaldırır.

## <a name="save-and-reset-a-workspace"></a>Çalışma alanını kaydetme ve sıfırlama

Varsayılan olarak, bir projeyi kapatıp yeniden açtığınızda RTVS çalışma alanı durumunu kaydetmez. Bununla birlikte, [çalışma alanı seçenekleri](options-for-r-tools-in-visual-studio.md#workspace)aracılığıyla bu davranışı değiştirebilirsiniz.

**R araçları**  >  **oturum**  >  **sıfırlama** komutu ve etkileşimli penceredeki araç çubuğunu Sıfırla düğmesi istediğiniz zaman çalışma alanı durumunu da sıfırlar. Uzak çalışma alanları ' nı sıfırlama, uzak sunucuya ilk kez bağlanırken oluşturulan kullanıcı profilini siler, bu da burada birikmiş dosyaları etkili bir şekilde siler.

## <a name="local-workspaces"></a>Yerel çalışma alanları

Yerel çalışma alanları listesinde bilgisayarınızda yüklü olan tüm R yorumlayıcıları görüntülenir.

Visual Studio başlatıldığında, **HKEY_LOCAL_MACHINE\Software\R-Core\\** kayıt defteri anahtarını arayarak yüklediğiniz tüm R sürümlerini otomatik olarak algılamaya çalışır. Bu denetim yalnızca başlangıçta yapıldığından, yeni bir R yorumlayıcısı yüklüyorsanız Visual Studio 'Yu yeniden başlatmanız gerekir.

RTVS, standart olmayan bir şekilde yüklenmiş bir R yorumlayıcısı algılamayabilir (örneğin, yalnızca bir yükleyiciyi çalıştırmak yerine dosyaları bir klasöre kopyalarken). Bu durumda, el ile yeni bir yerel R çalışma alanını aşağıdaki şekilde oluşturun:

1. Çalışma alanları penceresindeki **Ekle** düğmesini seçin.
1. Yeni çalışma alanı için bir ad girin.
1. R kök klasörünün yolunu girin, bu, yorumlayıcıya sahip *bin* klasörünü IÇEREN ve rtvs başladığında yorumlayıcıya geçirilecek herhangi bir isteğe bağlı komut satırı bağımsız değişkenle birlikte.
1. İşiniz bittiğinde **Kaydet**’i seçin.

![Yeni çalışma alanı ekleme](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Uzak çalışma alanları

Uzak çalışma alanları, uzak bir bilgisayardaki R oturumuna bağlanmanızı sağlar. (Bir bilgisayarın bu amaçla nasıl yapılandırılacağı hakkında [uzak çalışma alanlarını ayarlama](setting-up-remote-r-workspaces.md) bölümüne bakın.)

Visual Studio, uzak çalışma alanlarını otomatik olarak algılamadığı için, önceki bölümde açıklandığı gibi, çalışma alanları penceresindeki **Ekle** düğmesini kullanarak bunları el ile eklemeniz gerekir. Bu durumda, uzak bilgisayarın URI 'sini yerel bir yol yerine girin.

> [!Important]
> Uzak çalışma alanları, uzak bilgisayarla iletişimin gizliliğini ve bütünlüğünü sağlamak için *https protokolünü kullanması gereken* bir URI tarafından tanımlanır. Visual Studio, HTTPS 'yi desteklemeyen bir uzak bilgisayara bağlanamaz.

> [!Note]
> Uzak çalışma alanları önizleme aşamasında etkin. Daha sonraki bir sürüm için dosya eşitleme sorununun daha iyi bir uygulaması üzerinde çalışıyoruz ve fikirlerinizi ve geri bildirimlerinizi hoş geldiniz.

## <a name="remote-workspace-logon"></a>Uzak çalışma alanı oturumu açma

Uzak çalışma alanında oturum açmak için bir Kullanıcı adı ve parola kullanmalısınız.

### <a name="logon-to-windows-workspace"></a>Windows çalışma alanında oturum açma

Uzak makineniz etki alanı hesabınızı kullanacak şekilde ayarlanırsa, uzak bir çalışma alanına erişmek için etki alanı oturum açma bilgilerini kullanabilirsiniz. Değilse, `machine-name\username` uzak makinedeki bir makine hesabını kullanarak oturum açmak için biçimi kullanmanız gerekir.

### <a name="logon-to-linux-workspace"></a>Linux çalışma alanında oturum açma

Linux hesabı kullanım biçiminde oturum açmak için `<<unix>>\username` . Örneğin, adıyla bir hesabınız varsa `ruser` , Kullanıcı adını olarak yazmanız gerekir `<<unix>>\ruser` .

## <a name="switch-between-workspaces"></a>Çalışma alanları arasında geçiş yapma

RTVS, aynı anda yalnızca tek bir çalışma alanına bağlanır. Bağlantılı çalışma alanı, çalışma alanları penceresinde küçük bir yeşil onay işaretiyle gösterilir. Varsayılan olarak, RTVS önceki bir oturumdaki en son açık yerel çalışma alanına bağlanır.

Etkin çalışma alanını değiştirmek için, istediğiniz çalışma alanının yanındaki mavi oku seçin. Bunun yapılması oturumunuzu kaydetmenizi ister, geçerli çalışma alanını sonlandırdıktan sonra yeni bir tane ile geçiş yapmanızı ister.

> [!Tip]
> Kaydet sorgusunu devre dışı bırakmak için, **R araçları**  >  **seçenekleri** komutunu seçin ve **çalışma alanlarını değiştirmeden önce onay iletişim kutusunu göster** seçeneğini belirleyin `No` . Bkz. [çalışma alanı seçenekleri](options-for-r-tools-in-visual-studio.md#workspace).

Kaldırılmış olan bir yerel çalışma alanına veya devre dışı bırakılmış bir uzak çalışma alanına geçiş yapmayı denerseniz, RTVS hiçbir çalışma alanına bağlanmayabilir. Sonuç olarak, etkileşimli pencereye kod girerken veya kodu çalıştırmaya çalıştığınızda bir hata görebilirsiniz:

![RTVS 'ye hiçbir çalışma alanı bağlandığında hata](media/workspaces-disconnected-interactive-window.png)

Bunu düzeltmek için, çalışma alanları penceresindeki başka bir çalışma alanına geçin. Kullanılabilir çalışma alanı yoksa bir R yorumlayıcı yüklemeniz gerekir. Visual Studio çalışırken bir yorumlayıcı yüklediyseniz Visual Studio 'Yu yeniden başlatmayı da deneyebilirsiniz.

### <a name="switch-to-a-remote-workspace"></a>Uzak çalışma alanına geçiş yap

RTVS, bir uzak çalışma alanına ilk kez bağlandığınızda kimlik bilgilerini ister, daha sonra bu kimlik bilgilerini (güvenli Windows kimlik bilgisi dolabı kullanarak) önbelleğe alır. Daha sonra uzak sunucuyla iletişim HTTPS üzerinden güvenli bir şekilde yapılır (gerekli olan).

Sunucunun yapılandırmasına bağlı olarak, bu okuma bağlantısı sırasında bir sertifika uyarısı görebilirsiniz, "uzak R Services tarafından sunulan güvenlik sertifikası gerçekten makineye bağlandığınızdan emin olmamıza izin vermez."

![Uzak bir çalışma alanına bağlanırken otomatik olarak imzalanan sertifika uyarısı](media/workspaces-remote-self-signed-certificate-warning.png)

Sertifika, bağlamaya çalıştığınız bilgisayar tarafından RTVS 'ye sunulan bir belgedir. Sertifika, bu bilgisayarın URI 'sini tanımlayan bir alan içerir. RTVS, sertifikadaki URI ile bilgisayara bağlanmak için kullanılan URI arasında bir uyumsuzluk algıladığında, sunucu güvenliğinin tehlikeye girmiş olabileceğini belirten bir hata ortaya çıkabilir.

Ancak, bu uyarı, güvenilen bir sağlayıcıdan bir tane kullanmak yerine, uzak bilgisayarda HTTPS 'yi etkinleştirmek için *otomatik olarak imzalanan bir sertifika* kullanılmışsa de görüntülenir. Daha fazla bilgi için bkz. [uzak çalışma alanlarını ayarlama](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Yerel ve uzak bilgisayarlardaki dizinler

Varsayılan olarak, yerel bir çalışma alanında yeni bir R yorumlayıcısı başlattığınızda, geçerli çalışma dizininiz *%USERPROFILE%\Documents* olur. **R araçları**  >  **çalışma dizini** komutlarını kullanarak veya Visual Studio Çözüm Gezgini bir projeye sağ tıklayıp, **çalışma dizinini ayarla** gibi komutları seçerek dizini dilediğiniz zaman değiştirebilirsiniz.

Bir uzak bilgisayara ilk kez bağlandığınızda, RTVS, çalışma dizinini bu profil altındaki *Belgeler* klasörüne ayarlayan kimlik bilgilerinizi temel alan kullanıcı profilini otomatik olarak oluşturur. Bu klasör, aynı kimlik bilgilerini kullanan sonraki tüm uzak oturumlarda kullanılır.

Sonuç olarak, kodunuzun çalıştırıldığı konum yerel ve uzak çalışma alanları arasında farklılık gösterebilir. Kodunuzda, her zaman veri dosyalarına göreli yollar kullanın ve bu sayede kodunuzun çalışma alanları arasında taşınabilir olması gerekir.

Ayrıca, uzak çalışma alanları ile, çalışma dizinindeki tüm dosyalar aynı kullanıcı profili için oturumlar arasında yerinde kalır. Daha önce belirtildiği gibi,   >    >  uzak bir çalışma alanı kullanırken R araçları oturum **sıfırlama** komutunu (veya etkileşimli penceredeki sıfırlama düğmesini) kullanarak bu dosyaları silebilirsiniz. Bu komut, yeniden bağlandığınızda yeniden oluşturulan kullanıcı profilini sunucudan siler.

## <a name="copy-project-files-to-remote-workspaces"></a>Proje dosyalarını uzak çalışma alanlarına Kopyala

Visual Studio 'da R projeleriyle çalışırken, uzak bir çalışma alanı kullanırken bile yerel bilgisayar her zaman en son proje dosyalarına sahiptir. Diğer bir deyişle, Visual Studio 'da bir projeyi açtığınızda (genellikle bu projeyi içeren bir çözümün açılması anlamına gelir), RTVS, projenin içeriğinin yerel bilgisayarda tamamen olduğunu varsayar. Uzak çalışma alanı, aslında projenin dosyaları için geçici bir ana bilgisayar ve koddan herhangi bir çıkış olur. Bu, örneğin, etkileşimli pencerede kullanarak bir dosya yüklenirken `source` , bu dosyanın zaten sağladığınız yoldaki uzak bilgisayarda olması gerektiği veya uzak R yorumlayıcısının geçerli çalışma dizininde olması gerektiği anlamına gelir ( `setwd()` işlevle ayarlanır).

Dosyalar uzak sunucuya aşağıdaki şekilde kopyalanır:

- Etkileşimli pencere aracılığıyla dosyalarla uzaktan çalışmak için, önce Çözüm Gezgini bu dosyalara (veya projeye) sağ tıklayıp **kaynak seçili**' i seçerek onları el ile kopyalamanız gerekir. Tek tek dosyalar için, sunucudaki çalışma dizinine kopyalanırlar; bir proje kopyalanırken, RTVS proje için bir klasör oluşturur.

- Ayrıca, Çözüm Gezgini ve ardından **kaynak seçili dosyalar**' ı seçerek dosyaları kopyalayabilirsiniz. Bu eylem, onları etkileşimli pencereye yükler ve orada çalıştırır. Oturum uzak bir bilgisayara bağlıysa, önce dosyalar kopyalanır.

- Rtvs, uzak bir çalışma alanına bağlandığında ve **F5** tuşuna bastığınızda **hata** ayıklama  >  **başlatma hata ayıklaması**' nı seçtiğinizde veya kodunuzu çalıştırmaya başladığınızda, rtvs varsayılan olarak projenin dosyasını uzak çalışma alanına otomatik olarak kopyalar (Bu davranışı denetleme için aşağıya bakın).

- Sunucuda zaten var olan dosyaların üzerine yazılır.

> [!Note]
> RTVS, tüm R işlev çağrılarını güvenilir bir şekilde ele amadığından, `source()` `runApp()` etkileşimli penceredeki veya (kılı uygulamalar için) gibi işlevleri çağırmak uzak çalışma  alanına dosya kopyalamaz.

[Proje özellikleri](r-projects-in-visual-studio.md#project-properties) , rtvs 'in bir proje çalıştırıldığında dosyaları kopyaladığını ve tam olarak hangi dosyaların kopyalandığını denetler. Bu sayfayı açmak için **Proje**  >  **(ad) Özellikler** menü komutunu seçin ya da Çözüm Gezgini ' de projeye sağ tıklayıp **Özellikler**' i seçin.

![Dosya Aktarım ayarlarıyla proje özellikleri çalıştırma sekmesi](media/workspaces-remote-file-transfer-filter-settings.png)

Burada, **Run on Files** özelliği, rtvs 'nin proje dosyalarını otomatik olarak kopyaladığını belirler. **Aktarılacak dosyalar** daha sonra tam olarak hangi dosyaların aktarılacağını filtreliyor. Varsayılan değer yalnızca kopyalama amaçlıdır *. R*, *. RMD*, *. SQL*, *. MD* ve *. cpp* dosyaları. Bu davranış, büyük veri dosyalarını her çalıştırmada yanlışlıkla sunucuya kopyalamayı önler.

## <a name="copy-files-from-a-remote-workspace"></a>Uzak çalışma alanından dosya kopyalama

R betiğiniz sunucuda dosyalar oluşturursa, bu dosyaları işlevini kullanarak istemciye geri kopyalayabilirsiniz `rtvs::fetch_file` . Bu işlev, en azından, bilgisayarınıza kopyalamak istediğiniz dosyanın uzak yolunu ve isteğe bağlı olarak bilgisayarınızdaki hedef yolu kabul eder. Bir yol belirtmezseniz, dosya *%userprofile%\indirmeleri* klasörünüze kopyalanır.
