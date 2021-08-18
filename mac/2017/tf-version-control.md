---
title: Team Foundation Sürüm Denetimi (TFVC)
description: Mac için Visual Studio (TFVC) Team Foundation Server/Azure DevOps Team Foundation Sürüm Denetimi bağlantı.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: e473746ce129352950a0e36ae25e44065facf5b780f45598c1366fdab9b39e9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121350637"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation Sürüm Denetimi'a bağlanma

> [!NOTE]
> macOS'ta en iyi sürüm denetimi deneyimi için, Team Foundation Sürüm Denetimi (TFVC) yerine Git'in kullanılması önerilir. Git, Mac için Visual Studio (TFS)/Team Foundation Server'de barındırılan depolar için varsayılan Azure DevOps. Git'i TFS/Azure DevOps hakkında daha fazla bilgi edinmek için [Git Deposu ayarlama makalesine](./set-up-git-repository.md) bakın.
>
> Daha önce Mac için Visual Studio için TFVC uzantısının önizleme sürümünü kullandıysanız, Mac için Visual Studio 2019'a yükseltirken artık desteklenmiyor.

Azure Repos iki sürüm denetimi modeli sağlar: [Git](/azure/devops/repos/git/?view=azure-devops&preserve-view=true), dağıtılmış bir sürüm denetim sistemi [ve merkezi bir Team Foundation Sürüm Denetimi](/azure/devops/repos/tfvc/index?view=azure-devops&preserve-view=true) denetim sistemi olan Team Foundation Sürüm Denetimi (TFVC).

Mac için Visual Studio Git depoları için tam destek sağlar, ancak TFVC ile çalışmak için bazı geçici çözümler gerektirir. Bugün sürüm denetimi için TFVC kullanıyorsanız, TFVC'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler:

* [Grafik Visual Studio Code için Azure Repos uzantısını ve uzantıyı kullanma](#use-visual-studio-code-and-the-azure-repos-extension)
* [Bağlan Komut Satırı İstemcisi 'Team Explorer Everywhere (TEE-CLC) kullanarak merkezinize bağlantı](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Bağlan uzantısını kullanarak (desteklenmeyen) TFVC Team Foundation Sürüm Denetimi ye Mac için Visual Studio](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Bu makalenin geri kalanında, yukarıda listelenen seçeneklerde size yol gösterilir.

## <a name="requirements"></a>Gereksinimler

* Visual Studio Community, Professional veya Mac Enterprise 7.8 ve sonraki sürümler.
* Azure DevOps Services, Team Foundation Server 2013 ve sonrası ya da Azure DevOps Server 2018 ve sonrası.
* Azure DevOps Services veya Team Foundation Server/Azure DevOps Server' Team Foundation Sürüm Denetimi.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code uzantısını Azure Repos kullanma

Dosyalarınızı sürüm denetiminde yönetmek için bir grafik arabirimle çalışmak için, Azure Repos için Visual Studio Code uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. Çalışmaya başlamanız için [Visual Studio Code](https://code.visualstudio.com) indirin ve sonra [uzantıyı yapılandırmayı Azure Repos öğrenin.](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere Komut Satırı İstemcisini kullanarak bağlanma

macOS Terminali'ni kullanamıyorsanız, Team Explorer Everywhere Komut Satırı İstemcisi (TEE-CLC) TFVC'de kaynağınıza bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantınızı ayarlamak ve değişiklikleri işlemek için aşağıdaki adımları takip edebilirsiniz.

### <a name="setting-up-the-tee-clc"></a>TEE-CLC'i ayarlama

TEE-CLC ile kurulum yapmak için iki yol vardır.

* İstemciyi Homebrew için Homebrew kullanın veya
* İstemciyi indirme ve el ile yükleme

En kolay çözüm, macOS için paket yöneticisi olan **HomeBrew'u** kullanmaktır. Bu yöntemi kullanarak yüklemek için:

1. macOS Terminal uygulamasını başlatma.
1. Terminali Homebrew sayfasındaki yönergeleri kullanarak Homebrew [yükleyin.](https://brew.sh/)
1. Yükleme Homebrew terminalden aşağıdaki komutu çalıştırın:`brew install tee-clc`

**TEE-CLC'nin el ile kurulumunu yapmak için:**

1. Team Explorer Everywhere GitHub(örneğin, bu yazma zamanında tee-clc-14.134.0.zip) Team Explorer Everywhere GitHub [tee-clc'nin](https://github.com/Microsoft/team-explorer-everywhere/releases) en son sürümünü indirin.
1. Dosyanın içeriğini .zip diskte bir klasöre ayıklar.
1. macOS Terminal uygulamasını açın ve komutunu `cd` kullanarak önceki adımda kullanılan klasöre geçin.
1. Klasöründen komutunu çalıştırarak komut satırı istemcisinin çalıştırılana kadar Java veya diğer `./tf` bağımlılıkları yüklemeniz isteniyor olabilir.

TEE-CLC yüklendikten sonra, istemci için lisans sözleşmesini görüntülemek ve kabul `tf eula` etmek için komutunu çalıştırabilirsiniz.

Son olarak, TFS/Azure DevOps ortamınız ile kimlik doğrulaması yapmak için sunucuda bir kişisel erişim belirteci oluşturmanız gerekir. Kişisel erişim [belirteçleriyle kimlik doğrulama hakkında daha fazla bilgi alın.](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true) TFVC ile kullanmak üzere kişisel erişim belirteci oluştururken, belirteci yapılandırarak Tam Erişim sağlamayı da tercih edersiniz.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>TeE-CLC kullanarak reponıza bağlanma

Kaynak kodunuzla bağlantı oluşturmak için önce komutunu kullanarak bir çalışma alanı oluşturmanız `tf workspace` gerekir. Örneğin, aşağıdaki komutlar "MyOrganization" Azure DevOps Services bir Kuruluşa bağlanabilirsiniz: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Ortam `TF_AUTO_SAVE_CREDENTIALS` ayarı kimlik bilgilerinizi kaydetmek için kullanılır, bu nedenle bunları birden çok kez girmeniz istendiğinde bu ayar kullanılır. Kullanıcı adı istendiğinde, önceki bölümde oluşturduğunuz kişisel erişim belirteci kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızı yerel bir klasöre eşlemek için komutunu `tf workfold` kullanırsınız. Aşağıdaki örnek, "MyRepository" TFVC projesinden "WebApp.Services" adlı bir klasörü eşler ve yerel ~/Projects/ klasörüne kopyalanır (geçerli kullanıcıların giriş klasöründeki "Projeler" klasörü) olarak ayarlanır.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanırsınız:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>TEE-CLC kullanarak değişiklikleri işleme

Dosyalarda değişiklik Mac için Visual Studio sonra, düzenlemelerinizi kontrol etmek için Terminal'e geri dönebilirsiniz. komutu, iade etmek üzere bekleyen değişiklikler listesine dosya eklemek için kullanılır ve komut, sunucuya gerçek `tf add` `tf checkin` iade işlemini gerçekleştirir. Komut, `checkin` açıklama eklemek veya ilgili iş öğesini ilişkilendirmek için parametreler içerir. Aşağıdaki kod parçacığında, bir klasördeki tüm dosyalar iadeye tekrar `WebApp.Services` tekrar eklenir. Ardından kod bir açıklamayla iade edilir ve "42" kimliğine sahip bir iş öğesiyle ilişkilendirilir.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada veya başka komutlarda bahsedilen komutlar hakkında daha fazla bilgi edinmek için Terminal'den aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Bağlan uzantısını kullanarak TFVC'Team Foundation Sürüm Denetimi kullanma

> [!NOTE]
> macOS'ta en iyi sürüm denetimi deneyimi için, Team Foundation Sürüm Denetimi (TFVC) yerine Git'in kullanılması önerilir. Git, Mac için Visual Studio (TFS)/Team Foundation Server'de barındırılan depolar için varsayılan Azure DevOps. Git'i TFS/Azure DevOps hakkında daha fazla bilgi edinmek için [Git Deposu ayarlama makalesine](./set-up-git-repository.md) bakın.
>
> Daha önce Mac için Visual Studio için TFVC uzantısının önizleme sürümünü kullandıysanız, Mac için Visual Studio 2019'a yükseltirken artık desteklenmiyor.

Mac için Visual Studio Uzantısı galerisinde, TFVC'ye bağlanmak için sınırlı destek sunan bir Team Foundation Sürüm denetimi uzantısı vardır. Uzantı desteklenmiyor ve bilinen birkaç sorun var, bu nedenle uzantıyı kullanırken deneyiminiz farklılık gösterebilir.

Uzantıyı yüklemek için Mac için Visual Studio'ı açın **ve Visual Studio > menüsünü** seçin. Galeri  **sekmesinde, TFS için Sürüm Denetimi > Team Foundation Sürüm Denetimi'ni** seçin ve Azure DevOps **Yükle... seçeneğine tıklayın:**

![Uzantı yöneticisi](media/tfvc-install.png)

Uzantıyı yüklemek için istemleri izleyin. Yüklendikten sonra IDE'leri yeniden başlatın.

### <a name="updating-the-extension"></a>Uzantıyı güncelleştirme

TFVC uzantısı güncelleştirmeleri düzenli aralıklarla yapılır. Güncelleştirmelere erişmek için **menüden Visual Studio > Uzantıları... seçeneğini** belirleyin ve Ardından Güncelleştirmeler **sekmesini** seçin. Listeden uzantıyı seçin ve Güncelleştir **düğmesine** basın:

Eski **paketi** kaldırıp yenisini yüklemek için sonraki iletişim kutusunda Yükle'ye basın.

### <a name="using-the-extension"></a>Uzantıyı kullanma

Uzantı yüklendikten sonra **TFS/> Aç... Azure DevOps > Menü öğesini** seçin.

![Uzantıyı açmak için menü öğesi](media/tfvc-source-control-explorer-devops.png)

Çalışmaya devam etmek için VSTS veya Team Foundation Server seçin ve Devam'a **basın:**

![Bağlan sunucuyla bağlantı](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos Kimlik doğrulama

Azure Repos'de barındırılan bir projeyi Azure Repos, aşağıdaki ayrıntıları girmeniz Microsoft hesabı istenir:

![Bağlan ile Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS Kimlik Doğrulaması

TFS'ye bağlanmak için sunucu ayrıntılarını ve hesap kimlik bilgilerinizi girin. NTLM kimlik doğrulamasını kullanmak için bir etki alanı girin, aksi takdirde temel kimlik doğrulamasını kullanmak için boş bırakın. Sunucu **Ekle'yi seçin:**

![TFS Sunucusunda oturum açma](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Proje seçme

Kimlik doğrulaması başarıyla tamamlandıktan sonra Kaynak Denetiminden Aç iletişim kutusunda hesapla ilişkili **depoların listesini** bulabilirsiniz:

![Projelerin görüntüleniyor olduğu Kaynak Denetimi iletişim kutusundan aç](media/tfvc-vsts-projects.png)

Bu iletişim kutusu aşağıdaki düğümlerle düzenlenmiştir:

- Azure DevOps veya koleksiyon – Bu, oturum açtığınız Microsoft hesabı bağlı tüm kuruluşları görüntüler.
- Projeler - Her kuruluşta veya koleksiyonda bir dizi proje olabilir. Proje, kaynak kodun, iş öğelerinin ve otomatik derlemelerin barındır bulunduğu alandır.

Bu noktada, bir proje veya kuruluşun adına göre arama ve filtreleme de sistesiniz.

#### <a name="adding-a-new-server"></a>Yeni sunucu ekleme

Listeye yeni bir sunucu eklemek için Kaynak **Denetiminden** Aç iletişim kutusundaki Konak **Ekle düğmesine** basın:

![Listeye yeni sunucu eklemek için vurgulanan ekle düğmesi](media/tfvc-add-new-server.png)

Listeden sağlayıcıyı seçin ve kimlik bilgilerinizi girin:

![Kaynak denetimi sağlayıcısı seçeneğini gösteren iletişim kutusu](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Yeni çalışma alanı oluşturma

Bir projeyle çalışmaya başlamak için bir çalışma alanına sahip olmak _gerekir._ Henüz bir çalışma alanınız yoksa, Kaynak Denetiminden  Aç iletişim kutusundaki Çalışma Alanı **açılır kutusundan bir çalışma alanı oluşturabilirsiniz:**

![Yeni çalışma alanı oluştur birleşik giriş kutusu seçeneği](media/tfvc-create-new-workspace.png)

Yeni çalışma alanınız için adı ve yerel yolu ayarlayın ve Çalışma Alanı **Oluştur'a tıklayın:**

![Yeni çalışma alanı için bir ad ve yerel yol girme](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Kaynak Kod Gezgini'ni kullanma

Bir çalışma alanı oluşturduktan ve projenizi eşleyenin ardından Kaynak Kod Gezgini ile _çalışmaya başlayabilirsiniz._

Kaynak Kod Gezgini'ni açmak için **TFS/> Menü öğesini Azure DevOps > Kaynak Denetim Gezgini** Denetimi'ni seçin.

Kaynak Kod Gezgini tüm eşlenen projelerde, dosyalarında ve klasörlerinde gezinmenizi sağlar. Ayrıca aşağıdakiler gibi tüm temel kaynak denetimi eylemlerini gerçekleştirmeye de olanak sağlar:

- En son sürümü al
- Belirli bir sürüme sahip olun
- Dosyaları kullanıma alma ve iade etme
- Dosyaları kilitleme ve dosyaların kilidini açma
- Dosyaları ekleme, silme ve yeniden adlandırma
- Geçmişi görüntüleme
- Değişiklikleri karşılaştırın.

Bu eylemlerin çoğu proje üzerinde bağlam eylemleri aracılığıyla kullanılabilir:

![Bir proje için bağlam menüsü eylemleri](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Çalışma alanlarını yönetme

Henüz çalışma alanı oluşturmadıysanız, Çalışma [](#creating-a-new-workspace) alanı oluşturma bölümünde açıklandığı gibi Kaynak Kod Gezgini'nin boş olduğunu fark edin:

![boş kaynak kodu gezgini](media/tfvc-setup-empty-sce.png)

Uzak projenizi yerel çalışma alanıyla ayarlamak için aşağıdaki adımları kullanın:

1. Birleşik giriş **kutusundan** Sunucu'ya tıklayın.
1. "Çalışma alanı yok" ifadesinin ve Yerel Yolun "Eşlenmemiş" olduğunu unutmayın. Yeni Çalışma **Alanı Oluştur iletişim** kutusunu görüntülemek için **Eşlenmemiş bağlantısını** seçin.
1. Çalışma alanı için bir ad girin ve ardından Çalışma Klasörü **Ekle'ye** tıklar ve projeyi bilgisayarınızda yerel bir klasöre eşler:

    ![Varsayılan seçenekleri gösteren yeni çalışma alanı oluştur iletişim kutusu](media/tfvc-workspace1.png)

1. Sunucunuzda yer alan tüm projeleri aynı çalışma alanına eşlemek için "$" klasörünü seçin veya tek bir proje seçin ve Tamam'a **tıklayın:**

    ![Tüm projeleri gösteren klasöre gözat iletişim kutusu](media/tfvc-workspace2.png)

1. Yerel makinenizin projelerini eşlemek istediğiniz konumu seçin ve Klasör **Seç'e tıklayın.**
1. Tamam'a basarak yeni çalışma alanının ayrıntılarını **onaylayın**

    ![Çalışma klasörü eklenmiş yeni çalışma alanı oluştur iletişim kutusu](media/tfvc-workspace3.png)

Çalışma alanınız ayar alındıktan sonra, Kaynak Kod Gezgini'nde Çalışma Alanlarını Yönet **düğmesine** tıklayarak değiştirilebilir veya kaldırılabilir.

![Çalışma Alanlarını Yönetme](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Sorun Giderme ve Bilinen Sorunlar

#### <a name="problems-using-basic-authentication"></a>Temel kimlik doğrulamasını kullanma sorunları

Bir sunucuyla kimlik doğrulaması yapmak için aşağıdaki seçenekler kullanılabilir:

- Oauth
- Temel
- Ntlm

Temel kimlik doğrulamasını kullanmak için, aşağıdaki **adımları izleyin ve** Azure DevOps Services kimlik doğrulaması kimlik bilgilerini etkinleştirmeniz gerekir:

1. Azure DevOps (https: \/ /dev.azure.com/{organization}/{project}) olarak oturum açın.

2. Kuruluş araç çubuğundan dişli simgesini ve ardından İlke'yi **seçin:**

    ![Dişli simgesinin Azure DevOps ve açılan menüde İlke'nin seçili olduğu kuruluş araç çubuğunun ekran görüntüsü.](media/tfvc-auth2.png)

3. Uygulama bağlantı ayarlarınızı gözden geçirme. Güvenlik ilkelerinize göre bu ayarları değiştirin:

    ![Uygulama Bağlantı İlkeleri ayarlarını gösteren Azure DevOps Services ekran görüntüsü.](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>TFVC'de hiçbir şey göremiyorum

Geliştirme makinenize Team Foundation Sürüm Denetimi (TFVC) ayarlamak için Çalışma  alanlarını yönetme bölümünde açıklandığı gibi bir çalışma [alanı oluşturmanız](#managing-workspaces) gerekir.

Bu Kaynak Denetim Gezgini Çalışma Alanlarını **Yönet Düğmesine** basın. Projeyi geliştirme makinenizin bir klasörüne eşlemek için adımları izleyin.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Projelerimin herhangi birini /hepsini göremiyorum

Kimlik doğrulama sonrasında projelerin listesini görüyor olun. Varsayılan olarak yalnızca TFS projeleri gösterilir. Diğer proje türlerini görmek için "Tüm projeleri gör" kutusunu işaretleyin.

Doğru ayrıcalıklara sahip değilsanız sunucuda yer alan projelerin görünmeyeceklerini unutmayın.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>"Çalışma alanı oluşturulamaz. Lütfen yeniden deneyin"

Yeni bir [çalışma alanı oluşturmak için](#creating-a-new-workspace)aşağıdaki koşulların karşı olduğundan emin olun:

- Çalışma alanı adı içinde geçersiz karakterlerin kullanımı yoktur.
- Ad 64 karakterden az olmalıdır.
- Yerel yol başka hiçbir çalışma alanı tarafından kullanılamaz.

### <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kullanarak TFVC'de kodunuzu geliştirin ve paylaşın (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)