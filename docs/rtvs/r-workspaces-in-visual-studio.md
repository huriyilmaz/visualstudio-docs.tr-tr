---
title: R çalışma alanları
description: Visual Studio'da çalışma alanlarını kullanarak R kodunun nerede çalıştığını denetleme.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 97ce4f226c39a20ad41c5977f800aa178450c69c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302653"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Çalışma alanlarıyla R kodunun nerede çalıştığını denetleme

R Tools for Visual Studio 'daki (RTVS) çalışma alanı, hem yerel hem de uzak bilgisayarlarda gerçekleşebilecek bir R oturumunun nerede çalıştığını yapılandırmanızı sağlar. Amaç, karşılaştırılabilir bir kullanıcı deneyimiyle üzerinde çalışmanızı sağlamaktır, bu da size daha güçlü bulut tabanlı bilgisayarlardan yararlanma olanağı sağlar.

**Çalışma Alanları** penceresini açmak için **R Tools** > **Windows** > **Çalışma Alanları** komutunu kullanın veya **Ctrl**+**9**tuşuna basın.

![Visual Studio için R Tools'ta Çalışma Alanları penceresi (VS2017)](media/workspaces-window.png)

Bu pencerede, yeşil onay işareti RTVS bağlı olduğu etkin çalışma alanı gösterir. Mavi ok seçilmesi etkin çalışma alanını ayarlar. Her çalışma alanının sağındaki ayarlar (dişli) simgesi, adını, konumunu ve komut satırı bağımsız değişkenlerini değiştirmenize olanak tanır. Kırmızı X, el ile eklenen çalışma alanını kaldırır.

## <a name="save-and-reset-a-workspace"></a>Çalışma alanını kaydetme ve sıfırlama

Varsayılan olarak, bir projeyi kapatıp yeniden açtığınızda RTVS çalışma alanı durumundan tasarruf etmez. Ancak, [Çalışma Alanı seçenekleri](options-for-r-tools-in-visual-studio.md#workspace)aracılığıyla bu davranışı değiştirebilirsiniz.

**Etkileşimli** > penceredeki R Tools**Session** > **Reset** komutu ve sıfırlama araç çubuğu düğmesi de çalışma alanı durumunu her zaman sıfırlar. Uzak çalışma alanlarında sıfırlama, uzak sunucuya ilk bağlanırken oluşturulan kullanıcı profilini siler ve bu da orada biriken dosyaları etkin bir şekilde siler.

## <a name="local-workspaces"></a>Yerel çalışma alanları

Yerel çalışma alanları listesi, bilgisayarınıza yüklediğiniz tüm R yorumlayıcılarını görüntüler.

Visual Studio başladığında, **HKEY_LOCAL_MACHINE\Software\R-Core\\ ** kayıt defteri anahtarına bakarak yüklediğiniz R sürümlerinin tümlerini otomatik olarak algılamaya çalışır. Bu denetim yalnızca başlangıçta yapıldığından, yeni bir R yorumlayıcısı yüklerseniz Visual Studio'yı yeniden başlatmanız gerekir.

RTVS standart olmayan bir şekilde yüklenmiş bir R yorumlayıcısı algılayamayabilir (örneğin, dosyaları yükleyici çalıştırmak yerine bir klasöre kopyalarken). Bu durumda, el ile aşağıdaki gibi yeni bir yerel R Çalışma Alanı oluşturun:

1. Çalışma Alanları penceresinde **Ekle** düğmesini seçin.
1. Yeni Çalışma Alanı için bir ad girin.
1. RTVS başlatıldığında yorumlayıcıya geçmek için isteğe bağlı komut satırı bağımsız değişkenleriyle birlikte, yorumlayıcıyla birlikte *çöp kutusu* klasörünü içeren R kök klasörüne giden yolu girin.
1. İşiniz bittiğinde **Kaydet**’i seçin.

![Yeni bir çalışma alanı ekleme](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Uzak çalışma alanları

Uzak çalışma alanları, uzak bir bilgisayardaki Bir R oturumuna bağlanmanızı sağlar. (Bkz. Bu amaçla bir bilgisayarı yapılandırmak için [uzak çalışma alanları ayarlayın.)](setting-up-remote-r-workspaces.md)

Visual Studio uzak çalışma alanlarını otomatik olarak algılamaz, bu nedenle önceki bölümde açıklandığı gibi Çalışma Alanları penceresindeki **Ekle** düğmesini kullanarak bunları el ile eklemeniz gerekir. Bu durumda, yerel bir yol yerine uzak bilgisayarın URI'sini girin.

> [!Important]
> Uzak çalışma alanları, uzak bilgisayarla iletişimin gizliliğini ve bütünlüğünü sağlamak için *HTTPS protokolünü kullanması gereken* bir URI tarafından tanımlanır. Visual Studio, HTTPS'yi desteklemeyen uzak bir bilgisayara bağlanamaz.

> [!Note]
> Uzak çalışma alanları etkin bir şekilde önizlemededir. Biz gelecekteki bir sürüm için dosya eşitleme sorunu daha iyi bir uygulama üzerinde çalışıyoruz ve fikir lerinizi ve geribildirim bekliyoruz.

## <a name="remote-workspace-logon"></a>Uzak Çalışma Alanı Girişi

Uzak çalışma alanına giriş yapmak için bir kullanıcı adı ve parola kullanmanız gerekir.

### <a name="logon-to-windows-workspace"></a>Windows çalışma alanına giriş

Uzak makineniz etki alanı hesabınızı kullanmak üzere düzenese, uzak bir çalışma alanına erişmek için etki alanı oturumunu kullanabilirsiniz. Değilse, o zaman uzak makine `machine-name\username` üzerinde bir makine hesabı kullanarak oturum açmak için biçimini kullanmanız gerekir.

### <a name="logon-to-linux-workspace"></a>Linux çalışma alanına giriş

Linux hesabı kullanım `<<unix>>\username` formatında oturum açmak için. Örneğin, ada `ruser`göre bir hesabınız varsa, kullanıcı adını `<<unix>>\ruser`.

## <a name="switch-between-workspaces"></a>Çalışma alanları arasında geçiş

RTVS aynı anda yalnızca tek bir çalışma alanına bağlıdır. Bağlı çalışma alanı, Çalışma Alanları penceresindeküçük bir yeşil onay işaretiyle gösterilir. Varsayılan olarak, RTVS önceki oturumdaki son açık yerel çalışma alanına bağlanır.

Etkin çalışma alanını değiştirmek için, istenen çalışma alanının yanındaki mavi oku seçin. Bunu yapmak, oturumunuzu kaydetmenizi ister, geçerli çalışma alanını sonlandırır ve sonra yenisine geçer.

> [!Tip]
> Kayıt istemini devre dışı bırakabilmek **için, R Araçları** > **Seçenekleri** komutunu seçin ve çalışma alanları seçeneğini ' ne geçmeden önce onay iletişim **kutusunu göster'i** `No`ayarlayın. Bkz. [Çalışma Alanı seçenekleri.](options-for-r-tools-in-visual-studio.md#workspace)

Kaldırılmamış yerel bir çalışma alanına veya kullanılamadığı uzak bir çalışma alanına geçmeye çalışırsanız, RTVS herhangi bir çalışma alanına bağlı olmayabilir. Sonuç olarak, etkileşimli pencereye kod girdiğinizde veya başka bir şekilde kodu çalıştırmayı denediğinizde bir hata görebilirsiniz:

![RTVS'ye hiçbir çalışma alanı bağlı olmadığında hata](media/workspaces-disconnected-interactive-window.png)

Bunu düzeltmek için Çalışma Alanları penceresindebaşka bir çalışma alanına geçin. Boş çalışma alanı yoksa, bir R yorumlayıcısı yüklemeniz gerekir. Visual Studio çalışırken bir tercüman yüklediyseniz Visual Studio'yı yeniden başlatmayı da deneyebilirsiniz.

### <a name="switch-to-a-remote-workspace"></a>Uzak bir çalışma alanına geçme

RTVS, uzak bir çalışma alanına ilk bağlandığınızda kimlik bilgilerini ister, ardından bu kimlik bilgilerini (güvenli Windows Kimlik Bilgileri Dolabını kullanarak) sonraki oturumlar için önbelleğe alırsa. Uzak sunucu ile iletişim daha sonra https üzerinden güvenli bir şekilde yapılır (gereklidir).

Sunucunun yapılandırmasına bağlı olarak, bağlanırken şöyle bir sertifika uyarısı görebilirsiniz: "Uzak R Hizmetleri tarafından sunulan güvenlik sertifikası, gerçekten makineye (ad) bağlandığınızı kanıtlamamıza izin vermiyor."

![Uzak bir çalışma alanına bağlanırken kendi imzalı sertifika uyarısı](media/workspaces-remote-self-signed-certificate-warning.png)

Sertifika, bağlanmaya çalıştığınız bilgisayar tarafından RTVS'ye sunulan bir belgedir. Sertifika, o bilgisayarın URI'sini tanımlayan bir alan içerir. Uyarı, RTVS sertifikadaki URI ile bilgisayara bağlanmak için kullanılan URI arasında bir uyumsuzluk algıladığında görünür ve sunucunun güvenliğinin tehlikeye atılmış olabileceğini gösterir.

Ancak, bu uyarı, güvenilir bir sağlayıcıdan kullanmak yerine uzak bilgisayarda HTTPS'yi etkinleştirmek için *kendi imzalı* bir sertifika kullanıldıysa da görünür. Daha fazla bilgi için [bkz.](setting-up-remote-r-workspaces.md)

## <a name="directories-on-local-and-remote-computers"></a>Yerel ve uzak bilgisayarlardaki dizinler

Varsayılan olarak, yerel bir çalışma alanında yeni bir R yorumlayıcısı başlattığınızda, geçerli çalışma dizini *%userprofile%\Documents*olur. **R Tools** > **Working Directory** komutlarını kullanarak veya Visual Studio Solution Explorer'da bir projeyi sağ tıklatarak ve Burada Çalışma **Dizini Ayarla**gibi komutları seçerek istediğiniz zaman dizini değiştirebilirsiniz.

Uzak bir bilgisayara ilk bağlandığınızda, RTVS otomatik olarak kimlik bilgilerinize dayalı bir kullanıcı profili oluşturur ve bu da çalışma dizini bu profilin altındaki *Belgeler* klasörüne ayarlar. Bu klasör, aynı kimlik bilgilerini kullanan sonraki tüm uzak oturumlar için kullanılır.

Sonuç olarak, kodlarınızın çalıştığı tam konum yerel ve uzak çalışma alanları arasında farklılık görebilir. Ardından, kodunuzda, kodunuzu çalışma alanlarında taşınabilir olacak şekilde veri dosyalarına ve bu şekilde göreli yollar kullanın.

Uzak çalışma alanlarında, çalışma dizinindeki tüm dosyaların aynı kullanıcı profili için oturumlar arasında yerinde kaldığını da unutmayın. Daha önce de belirtildiği gibi, uzak bir çalışma alanı kullanırken **R Tools** > **Session** > **Reset** komutunu (veya etkileşimli penceredeki sıfırlama düğmesini) kullanarak bu dosyaları silebilirsiniz. Bu komut, yeniden bağlandığınızda yeniden oluşturulan sunucudan kullanıcı profilini yine siler.

## <a name="copy-project-files-to-remote-workspaces"></a>Proje dosyalarını uzak çalışma alanlarına kopyalama

Visual Studio'da R projeleri ile çalışırken, uzak bir çalışma alanı kullanıyorsanız bile yerel bilgisayar her zaman en son proje dosyalarına sahiptir. Diğer bir deyişle, Visual Studio'da bir proje açtığınızda (genellikle bu projeyi içeren bir çözüm açmak anlamına gelir), RTVS projenin içeriğinin tamamen yerel bilgisayarda bulunduğunu varsayar. Uzak çalışma alanı, aslında, projenin dosyaları ve koddan herhangi bir çıktı için geçici bir ana bilgisayardır. Bu, örneğin, etkileşimli pencerede `source` bir dosya yüklerken, bu dosyanın sağladığınız yolda uzak bilgisayarda zaten olması gerektiği veya uzak R yorumlayıcısının `setwd()` (işlevle birlikte ayarlanmış) geçerli çalışma dizininde olması gerektiği anlamına gelir.

Dosyalar aşağıdaki gibi uzak sunucuya kopyalanır:

- Etkileşimli pencereden dosyalarla uzaktan çalışmak için, önce Solution Explorer'da bu dosyaları (veya projeyi) sağ tıklatarak ve **Kaynak Seçili'ni**seçerek dosyaları el ile kopyalamanız gerekir. Tek tek dosyalar için, sunucudaki çalışma dizinine kopyalanırlar; bir proje kopyalarken, RTVS proje için bir klasör oluşturur.

- Ayrıca, Solution Explorer'da sonrayı seçip **kaynak seçili dosyaları(lar)** seçerek dosyaları kopyalayabilirsiniz. Bu eylem onları etkileşimli pencereye yükler ve orada çalıştırır. Oturum uzak bir bilgisayara bağlıysa, dosyalar önce orada kopyalanır.

- RTVS uzak bir çalışma alanına bağlandığında ve **F5**tuşuna bastığınızda, **Hata Ayıklama** > **Başlatma Hata Ayıklama'yı**seçin veya kodunuzu çalıştırmaya başlayın, RTVS varsayılan olarak projenin dosyasını otomatik olarak uzak çalışma alanına kopyalar (bu davranışı nasıl kontrol edebilirsiniz) bölümüne bakın.

- Sunucuda zaten var olan tüm dosyalar üzerine yazılır.

> [!Note]
> RTVS tüm R işlev çağrılarını güvenilir bir `source()` şekilde `runApp()` engelleyemediğinden, etkileşimli penceredeki (Shiny uygulamaları için) gibi arama işlevleri dosyaları uzak çalışma alanına *kopyalamaz.*

[Proje özellikleri,](r-projects-in-visual-studio.md#project-properties) bir proje çalıştırıldığında RTVS'nin dosyaları kopyalayıp kopyalamadığını ve tam olarak hangi dosyaların kopyalanmasını denetler. Bu sayfayı açmak için **Project** > **(name) Properties** menüsü komutunu seçin veya Solution Explorer'da projeyi sağ tıklatın ve **Özellikler'i**seçin.

![Proje özellikleri dosya aktarım ayarlarıyla sekme çalışır](media/workspaces-remote-file-transfer-filter-settings.png)

Burada, **çalıştırılan özellikteki Aktarım dosyaları,** RTVS'nin proje dosyalarını otomatik olarak kopyalayıp kopyalamayacağını belirler. Değer **aktaracak dosyalar,** sonra tam olarak hangi dosyaların aktarıldığını filtreler. Varsayılan yalnızca *kopyalamaktır. R*, *. Rmd*, *.sql*, *.md*, ve *.cpp* dosyaları. Bu davranış, her çalıştırmada büyük veri dosyalarını yanlışlıkla sunucuya kopyalamaktan kaçınır.

## <a name="copy-files-from-a-remote-workspace"></a>Dosyaları uzak bir çalışma alanından kopyalama

R komut dosyanız sunucuda dosya oluşturuyorsa, `rtvs::fetch_file` bu dosyaları işlevi kullanarak istemciye geri kopyalayabilirsiniz. Bu işlev, en azından bilgisayarınıza kopyalamak istediğiniz dosyaya giden uzak yolu ve isteğe bağlı olarak bilgisayarınızdaki hedef yolu kabul eder. Bir yol belirtmezseniz, dosya *%userprofile%\Downloads* klasörüne kopyalanır.
