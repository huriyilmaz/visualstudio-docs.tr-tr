---
title: Team Foundation Sürüm Denetimi (tfvc)
description: Mac için Visual Studio Team Foundation Server/Azure DevOps Team Foundation Sürüm Denetimi (tfvc) ile bağlama.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: b9aa9b718ad4618502a58185c27333d689c74300
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962313"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation Sürüm Denetimi bağlanılıyor

> [!NOTE]
> macos üzerinde en iyi sürüm denetimi deneyimi için Team Foundation Sürüm Denetimi (tfvc) yerine Git kullanmanız önerilir. Git Mac için Visual Studio desteklenir ve Team Foundation Server (TFS)/Azure DevOps barındırılan depolar için varsayılan seçenektir. git 'i TFS/Azure DevOps kullanma hakkında daha fazla bilgi için bkz. [git deposu ayarlama](./set-up-git-repository.md) makalesi.
>
> Mac için Visual Studio için tfvc uzantısının önizleme sürümünü daha önce kullandıysanız, Mac için Visual Studio 2019 sürümüne yükseltirken artık bu desteklenmez.

Azure Repos, bir merkezi sürüm denetim sistemi olan [Git](/azure/devops/repos/git/?view=azure-devops&preserve-view=true), dağıtılmış sürüm denetim sistemi ve [Team Foundation Sürüm Denetimi](/azure/devops/repos/tfvc/index?view=azure-devops&preserve-view=true) (tfvc) olmak üzere iki model sürümü sağlar.

Mac için Visual Studio, Git depoları için tam destek sağlar, ancak tfvc ile çalışmak için bazı geçici çözümler gerektirir. Sürüm denetimi için TFVC 'yi bugün kullanıyorsanız, TFVC 'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler aşağıda verilmiştir:

* [grafik kullanıcı arabirimi için Visual Studio Code ve Azure Repos uzantısını kullanın](#use-visual-studio-code-and-the-azure-repos-extension)
* [Team Explorer Everywhere komut satırı istemcisini (t-CLC) kullanarak depoya Bağlan](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Mac için Visual Studio için (desteklenmeyen) Team Foundation Sürüm Denetimi uzantısı kullanılarak tfvc 'ye Bağlan](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Bu makalenin geri kalanında yukarıda listelenen seçeneklere adım adım yol gösterilir.

## <a name="requirements"></a>Gereksinimler

* Mac 7,8 ve sonraki sürümleri için Visual Studio Community, Professional veya Enterprise.
* Azure DevOps Services, Team Foundation Server 2013 ve üzeri ya da 2018 ve üzeri Azure DevOps Server.
* Azure DevOps Services veya Team Foundation Server/Azure DevOps Server bir proje Team Foundation Sürüm Denetimi kullanacak şekilde yapılandırıldı.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code ve Azure Repos uzantısını kullanın

sürüm denetimindeki dosyalarınızı yönetmek için bir grafik arabirimle çalışmak isterseniz, Visual Studio Code için Azure Repos uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. başlamak için [Visual Studio Code](https://code.visualstudio.com) indirin ve [Azure Repos uzantısının nasıl yapılandırılacağını](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)öğrenin.

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere komut satırı istemcisini kullanarak bağlanma

macos terminalini rahat kullanıyorsanız, Team Explorer Everywhere komut satırı istemcisi (t-CLC), tfvc 'de kaynağınıza bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantısını kurmak ve değişiklikleri kaydetmek için aşağıdaki adımları izleyebilirsiniz.

### <a name="setting-up-the-tee-clc"></a>T-CLC ayarlanıyor

T-CLC ile kurulum almanın iki yolu vardır.

* istemciyi yüklemek için Homebrew kullanın veya
* İstemciyi indirip el ile yükleme

En kolay çözüm, macOS için bir paket yöneticisi olan **HomeBrew**' ı kullanmaktır. Bu yöntemi kullanarak yüklemek için:

1. MacOS Terminal uygulamasını başlatın.
1. Terminal ve [Homebrew giriş sayfasındaki](https://brew.sh/)yönergeleri kullanarak Homebrew 'yi yükler.
1. Homebrew yüklendikten sonra terminalinizden aşağıdaki komutu çalıştırın:`brew install tee-clc`

**T-CLC ' i el ile ayarlamak** için:

1. Team Explorer Everywhere GitHub deposunun yayınlar sayfasından [t-clc ' un en son sürümünü indirin](https://github.com/Microsoft/team-explorer-everywhere/releases) (örn. bu yazma sırasında tee-clc-14.134.0.zip).
1. .zip içeriğini diskteki bir klasöre ayıklayın.
1. MacOS Terminal uygulamasını açın ve `cd` önceki adımda kullandığınız klasöre geçmek için komutunu kullanın.
1. Klasörü içinden `./tf` komut satırı istemcisinin çalıştıracağınızı sınamak için komutunu çalıştırın, Java veya başka bağımlılıklar yüklemek isteyip istemediğiniz sorulur.

T-CLC yüklendikten sonra, `tf eula` istemcinin lisans sözleşmesini görüntülemek ve kabul etmek için komutunu çalıştırabilirsiniz.

son olarak, TFS/Azure DevOps ortamınızda kimlik doğrulamak için sunucuda bir kişisel erişim belirteci oluşturmanız gerekir. [Kişisel erişim belirteçleriyle kimlik doğrulama](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true)hakkında daha fazla bilgi edinin. TFVC ile kullanmak için bir kişisel erişim belirteci oluştururken, belirteci yapılandırırken tam erişim sağladığınızdan emin olun.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Depoya bağlanmak için t-CLC kullanma

Kaynak kodunuza bağlanmak için, önce komutunu kullanarak bir çalışma alanı oluşturmanız gerekir `tf workspace` . örneğin, aşağıdaki komutlar "myorganleştirme" adlı Azure DevOps Services bir kuruluşa bağlanır: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS`Ortam ayarı, kimlik bilgilerinizi birden çok kez girmeniz istenmeyecek şekilde kaydetmek için kullanılır. Bir Kullanıcı adı sorulduğunda, önceki bölümde oluşturduğunuz kişisel erişim belirtecini kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızın bir yerel klasöre eşlenmesini oluşturmak için `tf workfold` komutunu kullanırsınız. Aşağıdaki örnekte "WebApp. Services" adlı bir klasör "MyRepository" TFVC projesinden eşlenir ve yerel ~/Projects/klasörüne (yani geçerli kullanıcıların giriş klasöründeki "projeler" klasörü) kopyalanmak üzere ayarlanır.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanın:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>T-CLC kullanarak değişiklikler yürütülüyor

Mac için Visual Studio dosyalarınızda değişiklikler yaptıktan sonra, düzenlemelerinizi denetlemek için terminale geri dönebilirsiniz. `tf add`Komut, iade edilecek bekleyen değişiklikler listesine dosya eklemek için kullanılır ve `tf checkin` komut sunucuda gerçek iade işlemini gerçekleştirir. `checkin`Komut, bir yorum eklemek veya ilgili bir iş öğesini ilişkilendirmek için parametreler içerir. Aşağıdaki kod parçacığında, bir klasördeki tüm dosyalar `WebApp.Services` , iade etme için yinelemeli olarak eklenir. Ardından, kod bir yorum ile iade edilir ve "42" KIMLIĞINE sahip bir iş öğesiyle ilişkilendirilir.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada bahsedilen komutlar veya diğerleri hakkında daha fazla bilgi edinmek için terminalde aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Team Foundation Sürüm Denetimi uzantısı kullanılarak tfvc 'ye Bağlan

> [!NOTE]
> macos üzerinde en iyi sürüm denetimi deneyimi için Team Foundation Sürüm Denetimi (tfvc) yerine Git kullanmanız önerilir. Git Mac için Visual Studio desteklenir ve Team Foundation Server (TFS)/Azure DevOps barındırılan depolar için varsayılan seçenektir. git 'i TFS/Azure DevOps kullanma hakkında daha fazla bilgi için bkz. [git deposu ayarlama](./set-up-git-repository.md) makalesi.
>
> Mac için Visual Studio için tfvc uzantısının önizleme sürümünü daha önce kullandıysanız, Mac için Visual Studio 2019 sürümüne yükseltirken artık bu desteklenmez.

Mac için Visual Studio uzantısı galerisinde, tfvc 'ye bağlanmak için sınırlı destek sunan bir Team Foundation sürüm denetimi uzantısı vardır. Uzantı desteklenmez ve bilinen birkaç soruna sahiptir, bu nedenle deneyiminiz kullanılırken farklılık gösterebilir.

uzantıyı yüklemek için Mac için Visual Studio başlatın ve **Visual Studio > uzantıları** menüsünü seçin. **galeri** sekmesinde, **TFS ve Azure DevOps için sürüm denetimi > Team Foundation Sürüm Denetimi** seçin ve ardından **ınstall...**' a tıklayın:

![Uzantı Yöneticisi](media/tfvc-install.png)

Uzantıyı yüklemek için istemleri izleyin. Yüklendikten sonra IDE 'yi yeniden başlatın.

### <a name="updating-the-extension"></a>Uzantı güncelleştiriliyor

TFVC uzantılı güncelleştirmeler düzenli aralıklarla yapılır. güncelleştirmelere erişmek için, menüden **Visual Studio > uzantıları...** öğesini seçin ve **güncelleştirmeler** sekmesini seçin. Listeden uzantıyı seçin ve **Güncelleştir** düğmesine basın:

Sonraki iletişim kutusunda **yükleme** ' ye basarak eski paketi kaldırın ve yenisini yükleme işlemini yapın.

### <a name="using-the-extension"></a>Uzantıyı kullanma

uzantı yüklendikten sonra, **TFS/Azure DevOps > uzak depodan aç... menü öğesinden > sürüm denetimini** seçin.

![Uzantıyı açmak için menü öğesi](media/tfvc-source-control-explorer-devops.png)

başlamak için VSTS veya Team Foundation Server seçin ve **devam**' a basın:

![sunucu ile Bağlan](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos Yetkilendirmesi

Azure Repos barındırılan bir proje seçtiğinizde, Microsoft hesabı ayrıntılarını girmeniz istenir:

![Azure Repos Bağlan](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS kimlik doğrulaması

TFS 'ye bağlanmak için sunucu ayrıntılarını ve hesap kimlik bilgilerinizi girin. NTLM kimlik doğrulamasını kullanmak için bir etki alanı girin, aksi takdirde temel kimlik doğrulamasını kullanmak için boş bırakın. **Sunucu Ekle**' yi seçin:

![TFS sunucusunda oturum açma](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Proje seçme

Kimliği başarıyla doğrulandıktan sonra **kaynak denetiminden Aç** iletişim kutusundan hesapla ilişkili depoların bir listesini görebilirsiniz:

![Projeler görüntülenirken kaynak denetimi iletişim kutusundan Aç](media/tfvc-vsts-projects.png)

Bu iletişim kutusu aşağıdaki düğümlerle düzenlenmiştir:

- Azure DevOps kuruluş veya koleksiyon – bu, ile oturum açtığınız Microsoft hesabı bağlı tüm kuruluşları görüntüler.
- Projeler-her bir kuruluşta veya koleksiyonda bir dizi projeniz olabilir. Proje, kaynak kodu, iş öğeleri ve otomatikleştirilmiş derlemelerin barındırıldığı yerdir.

Bu noktada, bir proje veya kuruluş adına göre arama ve filtreleme yapabilirsiniz.

#### <a name="adding-a-new-server"></a>Yeni sunucu ekleme

Listeye yeni bir sunucu eklemek için, **kaynak denetiminden Aç** Iletişim kutusunda **konak Ekle** düğmesine basın:

![Listeye yeni sunucu eklemek için vurgulanan Ekle düğmesi](media/tfvc-add-new-server.png)

Listeden sağlayıcıyı seçin ve kimlik bilgilerinizi girin:

![Kaynak denetimi sağlayıcısı için seçeneği gösteren iletişim kutusu](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Yeni bir çalışma alanı oluşturma

Bir projeyle çalışmaya başlamak için bir çalışma alanına sahip olmak _gerekir._ Henüz bir çalışma alanınız yoksa, Kaynak Denetiminden  Aç iletişim kutusundaki Çalışma Alanı **açılır kutusundan bir çalışma alanı oluşturabilirsiniz:**

![Yeni çalışma alanı oluştur birleşik giriş kutusu seçeneği](media/tfvc-create-new-workspace.png)

Yeni çalışma alanınız için adı ve yerel yolu ayarlayın ve Çalışma Alanı **Oluştur'a tıklayın:**

![Yeni çalışma alanı için bir ad ve yerel yol girme](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Kaynak Kod Gezgini'ni kullanma

Bir çalışma alanı oluşturduktan ve projenizi eşleyenin ardından Kaynak Kod Gezgini ile _çalışmaya başlayabilirsiniz._

Kaynak Kod Gezgini'ni açmak için **TFS/> Sürüm** Denetimi Azure DevOps > Kaynak Denetim Gezgini öğesini seçin.

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

Geliştirme makinenize Team Foundation Sürüm Denetimi (TFVC) ayarlamak için Çalışma  alanlarını yönetme bölümünde açıklandığı gibi bir [çalışma alanı oluşturmanız](#managing-workspaces) gerekir.

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