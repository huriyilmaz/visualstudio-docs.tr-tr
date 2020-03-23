---
title: Takım Temel Sürüm Kontrolü (TFVC)
description: Visual Studio for Mac'ten Team Foundation Server/Azure DevOps'e Team Foundation Sürüm Kontrolü (TFVC) ile bağlanma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: b7b160d58cead031a0eece2a522501d8c2060bd2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985204"
---
# <a name="connecting-to-team-foundation-version-control"></a>Takım Temel Sürüm Kontrolüne Bağlanma

> [!NOTE]
> macOS'taki en iyi sürüm kontrol deneyimi için, Team Foundation Version Control (TFVC) yerine Git'i kullanmanızı öneririz. Git, Mac için Visual Studio'da desteklenir ve Team Foundation Server (TFS)/Azure DevOps'te barındırılan depolar için varsayılan seçenektir. TFS/Azure DevOps ile Git'i kullanma hakkında daha fazla bilgi edinmek için [Git Deposu](/visualstudio/mac/set-up-git-repository) oluşturma makalesine bakın.
>
> Daha önce Mac için Visual Studio için TFVC uzantısı önizleme sürümü kullandıysanız, Mac için Visual Studio 2019'a yükseltilirken artık desteklenmez.

Azure Repos iki sürüm denetimi modeli sağlar: [Dağıtılmış](/azure/devops/repos/git/?view=azure-devops)sürüm denetim sistemi Git ve merkezi sürüm kontrol sistemi [Olan Team Foundation Version Control](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC).

Mac için Visual Studio Git depoları için tam destek sağlar, ancak TFVC ile çalışmak için bazı geçici çözüm gerektirir. Bugün sürüm kontrolü için TFVC kullanıyorsanız, TFVC'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler şunlardır:

* [Grafiksel bir bilgi edinin için Visual Studio Code ve Azure Depoları uzantısını kullanma](#use-visual-studio-code-and-the-azure-repos-extension)
* [Team Explorer Everywhere Komut Satırı İstemcisini (TEE-CLC) kullanarak repo'nuza bağlanın](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Mac için Visual Studio için (desteklenmeyen) Team Foundation Sürüm Kontrolü uzantısını kullanarak TFVC'ye bağlanın](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Bu makalenin geri kalanı yukarıda listelenen seçenekler üzerinden size yol eder.

## <a name="requirements"></a>Gereksinimler

* Visual Studio Community, Professional veya Enterprise mac sürüm 7.8 ve sonrası için.
* Azure DevOps Hizmetleri, Team Foundation Server 2013 ve sonrası veya Azure DevOps Server 2018 ve sonrası.
* Azure DevOps Hizmetleri veya Team Foundation Server/Azure DevOps Server'da yer alan ve Team Foundation Sürüm Denetimini kullanacak şekilde yapılandırılan bir proje.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Kodu ve Azure Depoları uzantısını kullanma

Dosyalarınızı sürüm denetiminde yönetmek için grafik arabirimiyle çalışmak isterseniz, Visual Studio Code için Azure Repos uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. Başlamak için [Visual Studio Code'u](https://code.visualstudio.com) indirin ve azure depo uzantısını nasıl [yapılandırıştırılacaöğrenin.](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Her Yerde Takım Gezgini Komut Satırı İstemcisini kullanarak bağlanma

macOS Terminali'ni kullanmaktan memnunsanız, Team Explorer Everywhere Komut Satırı İstemi (TEE-CLC) Kaynağınıza TFVC'de bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantınızı kurmak ve değişiklikler gerçekleştirmek için aşağıdaki adımları izleyebilirsiniz.

### <a name="setting-up-the-tee-clc"></a>TEE-CLC'nin kurulumu

TEE-CLC ile kurulum almanın iki yolu vardır.

* İstemciyi yüklemek için Homebrew'i kullanma veya
* İstemciyi indirin ve el ile kurun

En kolay çözüm **HomeBrew kullanıyor**, macOS için bir paket yöneticisi. Bu yöntemi kullanarak yüklemek için:

1. macOS Terminaluygulamasını başlatın.
1. Homebrew'i Terminal'i ve [Homebrew ana sayfasındaki](https://brew.sh/)talimatları kullanarak yükleyin.
1. Homebrew yüklendikten sonra Terminalinizden aşağıdaki komutu çalıştırın:`brew install tee-clc`

**TEE-CLC'yi el ile kurmak**için:

1. Team Explorer Everywhere GitHub repo'nun sürümler sayfasından [tee-clc'nin en son sürümünü indirin](https://github.com/Microsoft/team-explorer-everywhere/releases) (örn. bu yazı nın yazıldığı sırada tee-clc-14.134.0.zip).
1. .zip'in içeriğini diskteki bir klasöre ayıklayın.
1. macOS Terminali uygulamasını açın `cd` ve önceki adımda kullandığınız klasöre geçmek için komutu kullanın.
1. Klasörün içinden, komut `./tf` satırı istemcisinin çalıştırabileceğini test etmek için komutu çalıştırın, Java veya diğer bağımlılıkları yüklemeniz istenebilir.

TEE-CLC yüklendikten sonra, istemcinin lisans `tf eula` sözleşmesini görüntülemek ve kabul etmek için komutu çalıştırabilirsiniz.

Son olarak, TFS/Azure DevOps ortamınızla kimlik doğrulaması yapmak için sunucuda kişisel erişim belirteci oluşturmanız gerekir. [Kişisel erişim belirteçleri ile kimlik doğrulama](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)hakkında daha fazla bilgi edinin. TFVC ile kullanılacak kişisel erişim jetonu oluştururken, belirteci yapılandırırken Tam Erişim sağladığından emin olun.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Repo'nuza bağlanmak için TEE-CLC'yi kullanma

Kaynak kodunuza bağlanmak için öncelikle komutu `tf workspace` kullanarak bir çalışma alanı oluşturmanız gerekir. Örneğin, aşağıdaki komutlar Azure DevOps Hizmetleri'ndeki "MyOrganization" adlı bir Kuruluşa bağlanır: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Ortam `TF_AUTO_SAVE_CREDENTIALS` ayarı, kimlik bilgilerinizi kaydetmek için kullanılır, böylece birden çok kez girmeniz istenmez. Bir kullanıcı adı istendiğinde, önceki bölümde oluşturduğunuz kişisel erişim belirteci kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızın yerel bir klasöre eşleneği oluşturmak `tf workfold` için komutu kullanırsınız. Aşağıdaki örnek, "MyRepository" TFVC projesinden "WebApp.Services" adlı bir klasörün haritasını çıkarır ve yerel ~/Projects/klasörüne (örneğin geçerli kullanıcıların ev klasöründe bir "Projeler" klasörüne) kopyalanacak şekilde ayarlar.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanırsınız:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>TEE-CLC kullanarak değişiklik yapmak

Mac için Visual Studio'da dosyalarınızda değişiklik yaptıktan sonra, denetimlerinizi iade etmek için Terminal'e geri dönebilirsiniz. Komut, `tf add` iade edilecek bekleyen değişiklikler listesine dosya eklemek için kullanılır `tf checkin` ve komut sunucuya gerçek iadeyi gerçekleştirir. Komut, `checkin` yorum eklemek veya ilgili bir iş öğesini ilişkilendirmek için parametreleri içerir. Aşağıdaki kod snippet'inde, `WebApp.Services` bir klasördeki tüm dosyalar iadeye özyinelemeli olarak eklenir. Daha sonra, kod bir açıklama ile iade edilir ve kimliği "42" olan bir iş öğesi ile ilişkili.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada belirtilen komutlar veya diğerleri hakkında daha fazla bilgi edinmek için Terminal'den aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Team Foundation Sürüm Denetimi uzantısını kullanarak TFVC'ye bağlanın

> [!NOTE]
> macOS'taki en iyi sürüm kontrol deneyimi için, Team Foundation Version Control (TFVC) yerine Git'i kullanmanızı öneririz. Git, Mac için Visual Studio'da desteklenir ve Team Foundation Server (TFS)/Azure DevOps'te barındırılan depolar için varsayılan seçenektir. TFS/Azure DevOps ile Git'i kullanma hakkında daha fazla bilgi edinmek için [Git Deposu](/visualstudio/mac/set-up-git-repository) oluşturma makalesine bakın.
>
> Daha önce Mac için Visual Studio için TFVC uzantısı önizleme sürümü kullandıysanız, Mac için Visual Studio 2019'a yükseltilirken artık desteklenmez.

Mac Extension galerisi için Visual Studio'da, TFVC'ye bağlanmak için sınırlı destek sunan bir Team Foundation Version denetim uzantısı vardır. Uzantı desteklenmez ve bilinen birkaç sorunu vardır, bu nedenle deneyiminiz kullanırken değişebilir.

Uzantıyı yüklemek için Visual Studio for Mac'i başlatın ve **Visual Studio > Uzantıları** menüsünü seçin. **Galeri** sekmesinde, **TFS ve Azure DevOps için Sürüm Denetimi > Team Foundation Sürüm Denetimi'ni** seçin ve **Yükle'yi tıklatın...**

![Uzatma yöneticisi](media/tfvc-install.png)

Uzantıyı yüklemek için istemleri izleyin. Yüklendikten sonra IDE'yi yeniden başlatın.

### <a name="updating-the-extension"></a>Uzantıyı güncelleştirme

TFVC uzantısına yapılan güncellemeler periyodik olarak yapılır. Güncelleştirmelere erişmek için menüden **Visual Studio > Uzantıları...** seçeneğini belirleyin ve **Güncellemeler** sekmesini seçin. Listedeki uzantıyı seçin ve **Güncelleştir** düğmesine basın:

Eski paketi kaldırmak ve yenisini yüklemek için bir sonraki iletişim kutusunda **Yükle'ye** basın.

### <a name="using-the-extension"></a>Uzantıyı kullanma

Uzantı yüklendikten sonra, **TFS/Azure DevOps > Uzaktan Depodan Aç... menü öğesini > Sürüm Denetimi'ni** seçin.

![Uzantıyı açmak için menü öğesi](media/tfvc-source-control-explorer-devops.png)

Başlamak için VSTS veya Team Foundation Server'ı seçin ve **Devam et:**

![Sunucuyla Bağlantı Kurun](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos Kimlik Doğrulaması

Azure Deposu'nda barındırılan bir proje seçtiğinizde, Microsoft hesap bilgilerinizi girmeniz istenir:

![Azure Depolarıyla Bağlantı Kurun](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS Kimlik Doğrulama

TFS'ye bağlanmak için sunucu ayrıntılarını ve hesap kimlik bilgilerinizi girin. NTLM kimlik doğrulamasını kullanmak için bir etki alanı girin, aksi takdirde temel kimlik doğrulamasını kullanmak için boş bırakın. **Sunucu Ekle'yi**seçin:

![TFS Sunucusunda Oturum Açma](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Proje seçme

Başarılı bir şekilde kimlik doğrulaması yaptıktan sonra, **Kaynak Denetiminden Açık** iletişim kutusunda hesapla ilişkili depoların listesini görebilirsiniz:

![Görüntülenen projelerle Kaynak Denetimi iletişim kutusundan aç](media/tfvc-vsts-projects.png)

Bu iletişim kutusu aşağıdaki düğümlerle düzenlenir:

- Azure DevOps kuruluşu veya koleksiyonu – Bu, oturum açtığınız Microsoft hesabına bağlı tüm kuruluşları görüntüler.
- Projeler - Her kuruluş veya koleksiyonda bir dizi projeniz olabilir. Proje, kaynak kodun, iş öğelerinin ve otomatik yapıların barındırıldığı yerdir.

Bu noktada, bir proje veya kuruluşun adına göre arama yapabilir ve filtreleyebilirsiniz.

#### <a name="adding-a-new-server"></a>Yeni bir sunucu ekleme

Listeye yeni bir sunucu eklemek için **Kaynak Denetimi'nden Aç** iletişim kutusundaki **Ana Bilgisayar Ekle** düğmesine basın:

![Listeye yeni sunucu eklemek için vurgulama ekle düğmesi](media/tfvc-add-new-server.png)

Listeden sağlayıcıyı seçin ve kimlik bilgilerinizi girin:

![Kaynak denetim sağlayıcısı için iletişim seçeneği gösterme](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Yeni bir çalışma alanı oluşturma

Bir projeyle çalışmaya başlamak için bir _çalışma alanına_sahip olmanız gerekir. Zaten bir çalışma alanınız yoksa, **Kaynak Denetimi'nden Aç** iletişim **kutusundaKi Çalışma Alanı** açılan kutusundan bir tane oluşturabilirsiniz:

![Yeni çalışma alanı combobox seçeneği oluşturma](media/tfvc-create-new-workspace.png)

Yeni çalışma alanınızın adını ve yerel yolunu ayarlayın ve **Çalışma Alanı Oluştur'u**seçin:

![Yeni çalışma alanı için bir ad ve yerel yol girme](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Kaynak Kodu Gezgini'ni kullanma

Bir çalışma alanı oluşturduktan ve projenizi eşledikten _sonra, Kaynak Kod Gezgini_ile çalışmaya başlayabilirsiniz.

Kaynak Kodu Gezgini'ni açmak için **TFS/Azure DevOps > Kaynak Denetimi Gezgini** menü öğesini > Sürüm Denetimi'ni seçin.

Kaynak Kodu Gezgini, eşlenen tüm projelerde, dosyalarında ve klasörlerinde gezinmenizi sağlar. Ayrıca, aşağıdakiler gibi tüm temel kaynak denetimi eylemlerini gerçekleştirmenize de olanak tanır:

- En son sürümü alın
- Belirli bir sürümü alın
- Dosyaları kullanıma alma ve iade etme
- Dosyaları kilitleme ve kilidini açma
- Dosyaları ekleme, silme ve yeniden adlandırma
- Geçmişi görüntüleme
- Değişiklikleri karşılaştırın.

Bu eylemlerin çoğu, projedeki bağlam eylemleri aracılığıyla kullanılabilir:

![Proje için bağlam menüsü eylemleri](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Çalışma alanlarını yönetme

Çalışma alanı oluşturma bölümünde açıklandığı gibi zaten [bir](#creating-a-new-workspace) çalışma alanı oluşturmadıysanız, Kaynak Kod Gezgini'nin boş olduğunu fark edeceksiniz:

![boş kaynak kodu gezgini](media/tfvc-setup-empty-sce.png)

Uzak projenizi yerel bir çalışma alanıyla ayarlamak için aşağıdaki adımları kullanın:

1. Combobox'tan **Sunucu'yu** seçin.
1. "Çalışma alanı yok" olduğunu ve Yerel Yolun "Eşlenmediğini" unutmayın. **Yeni Çalışma Alanı Oluştur** iletişim kutusunu görüntülemek için **Eşlendirilmeyecek** bağlantısını seçin.
1. Çalışma alanı için bir ad sağlayın ve ardından projeyi bilgisayarınızdaki yerel bir klasörle eşlemek için **Çalışma Klasörü Ekle'yi** tıklatın:

    ![Varsayılan seçenekleri gösteren yeni bir çalışma alanı iletişim kutusu oluşturma](media/tfvc-workspace1.png)

1. Sunucunuzdaki tüm projeleri aynı çalışma alanına eşlemek için "$" klasörünü seçin veya tek bir proje seçin ve **Tamam'ı**tıklatın:

    ![Tüm projeleri gösteren klasör iletişim günlüğüne göz atın](media/tfvc-workspace2.png)

1. Proje(ler) ile eşlenebilmek istediğiniz yerel makinenizdeki konumu seçin ve **Klasörü Seç'i**tıklatın.
1. **Tamam** tuşuna basarak yeni çalışma alanının ayrıntılarını doğrulayın

    ![Çalışma klasörü eklendi ile yeni çalışma alanı iletişim kutusu oluşturma](media/tfvc-workspace3.png)

Çalışma alanınız ayarlandıktan sonra, Kaynak Kodu Gezgini'ndeki **Çalışma Alanlarını Yönet** düğmesini tıklatarak değiştirilebilir veya kaldırılabilir.

![Çalışma Alanlarını Yönetme](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Sorun Giderme ve Bilinen Sorunlar

#### <a name="problems-using-basic-authentication"></a>Temel kimlik doğrulamayı kullanma sorunları

Aşağıdaki seçenekler bir sunucu ile kimlik doğrulaması için kullanılabilir:

- Oauth
- Temel
- Ntlm

Temel kimlik doğrulamayı kullanmak için Aşağıdaki adımları izleyerek Azure DevOps Hizmetlerinde **Alternatif kimlik doğrulama kimlik bilgilerini** etkinleştirmek gerekir:

1. Azure DevOps kuruluşunuzda sahibi olarak oturum\/açın (https: /dev.azure.com/{organization}/{project}).

2. Kuruluş araç çubuğunuzdan vites simgesini seçin ve **Politika'yı**seçin:

    ![İlke ayarları seçeneği seçili](media/tfvc-auth2.png)

3. Uygulama bağlantı ayarlarınızı gözden geçirin. Güvenlik ilkelerinize göre bu ayarları değiştirin:

    ![İlke ayarları seçeneği seçili](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Ben TFVC bir şey görmüyorum

Geliştirme makinenizde Team Foundation Sürüm Denetimi 'ni (TFVC) ayarlamak için, [çalışma alanlarını yönetme](#managing-workspaces) bölümünde açıklandığı gibi bir çalışma alanı oluşturmanız **gerekir.**

Kaynak Denetimi Gezgini'nde **Çalışma Alanlarını Yönet** düğmesine basın. Projeyi geliştirme makinenizdeki bir klasöre eşlemek için adımları izleyin.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Ben herhangi bir / tüm projeleri görmüyorum

Kimlik doğrulaması yaptıktan sonra projelerin listesini görmeniz gerekir. Varsayılan olarak, yalnızca TFS projeleri gösterilir. Diğer proje türlerini görmek için "Tüm projeleri gör" kutusunu işaretleyin.

Doğru ayrıcalıklara sahip değilseniz, sunucudaki projelerin görüntülenmeyeceğini unutmayın.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Ben hata alıyorum "Çalışma alanı oluşturamıyorum. Lütfen, tekrar deneyin"

[Yeni bir çalışma alanı oluşturmaya](#creating-a-new-workspace)çalışırken, aşağıdaki koşulların karşılandıktan emin olmalısınız:

- Çalışma alanı adında geçersiz karakterler kullanılmaz.
- Ad 64 karakterden az olmalıdır.
- Yerel yol başka bir çalışma alanı tarafından kullanılamaz.

### <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'yı kullanarak kodunuzu TFVC'de geliştirin ve paylaşın (Windows'da)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)