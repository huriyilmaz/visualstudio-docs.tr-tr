---
title: Team Foundation Sürüm Denetimi (TFVC)
description: Team Foundation Sürüm Denetimi (TFVC) ile Mac için Visual Studio Team Foundation Server/Azure DevOps 'a bağlanma.
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: e45f80ab1a5aab4969b01a2fddcfd88d9dc4eff7
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73716125"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation Sürüm Denetimi bağlanılıyor

> [!NOTE]
> MacOS üzerinde en iyi sürüm denetimi deneyimi için Team Foundation Sürüm Denetimi (TFVC) yerine git kullanmanız önerilir. Git Mac için Visual Studio desteklenir ve Team Foundation Server (TFS)/Azure DevOps içinde barındırılan depolar için varsayılan seçenektir. Git 'i TFS/Azure DevOps ile kullanma hakkında daha fazla bilgi edinmek için [Git deposu ayarlama](/visualstudio/mac/set-up-git-repository) makalesini inceleyin.
>
> Mac için Visual Studio için TFVC uzantısının önizleme sürümünü daha önce kullandıysanız, Mac için Visual Studio 2019 ' e yükseltirken artık bu desteklenmez.

Azure Repos, bir merkezi sürüm denetim sistemi olan [Git](/azure/devops/repos/git/?view=azure-devops), dağıtılmış sürüm denetim sistemi ve [Team Foundation sürüm denetimi](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC) olmak üzere iki model sürümü sağlar.

Mac için Visual Studio, git depoları için tam destek sağlar, ancak TFVC ile çalışmak için bazı geçici çözümler gerektirir. Sürüm denetimi için TFVC 'yi bugün kullanıyorsanız, TFVC 'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler aşağıda verilmiştir:

* [Grafik Kullanıcı arabirimi için Visual Studio Code ve Azure Repos uzantısını kullanın](#use-visual-studio-code-and-the-azure-repos-extension)
* [Team Explorer Everywhere komut satırı Istemcisini (t-CLC) kullanarak depoya bağlanma](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Mac için Visual Studio için (desteklenmeyen) Team Foundation Sürüm Denetimi uzantısını kullanarak TFVC 'ye bağlanma](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Bu makalenin geri kalanında yukarıda listelenen seçeneklere adım adım yol gösterilir.

## <a name="requirements"></a>Gereksinimler

* Mac için Visual Studio Community, Professional veya Enterprise sürüm 7,8 ve üzeri.
* Azure DevOps Services, Team Foundation Server 2013 ve üzeri ya da 2018 ve üzeri Azure DevOps Server.
* Azure DevOps Services veya Team Foundation Server/Azure DevOps Server bir proje Team Foundation Sürüm Denetimi kullanacak şekilde yapılandırıldı.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code ve Azure Repos uzantısını kullanın

Sürüm denetimindeki dosyalarınızı yönetmek için bir grafik arabirimle çalışmak isterseniz, Visual Studio Code için Azure Repos uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. Başlamak için [Visual Studio Code](https://code.visualstudio.com) indirin ve [Azure Repos uzantısının nasıl yapılandırılacağını](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)öğrenin.

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere komut satırı Istemcisini kullanarak bağlanma

MacOS terminalini rahat kullanıyorsanız, Team Explorer Everywhere komut satırı Istemcisi (t-CLC), TFVC 'de kaynağınıza bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantısını kurmak ve değişiklikleri kaydetmek için aşağıdaki adımları izleyebilirsiniz.

### <a name="setting-up-the-tee-clc"></a>T-CLC ayarlanıyor

T-CLC ile kurulum almanın iki yolu vardır.

* İstemcisini yüklemek için homebrew kullanın veya
* İstemciyi indirip el ile yükleme

En kolay çözüm, macOS için bir paket yöneticisi olan **HomeBrew**' ı kullanmaktır. Bu yöntemi kullanarak yüklemek için:

1. MacOS Terminal uygulamasını başlatın.
1. Terminal ve [homebrew giriş sayfasındaki](https://brew.sh/)yönergeleri kullanarak Homebrew 'ı yükler.
1. Homebrew yüklendikten sonra Terminalinizden şu komutu çalıştırın: `brew install tee-clc`

**T-CLC ' i el ile ayarlamak**için:

1. Team Explorer Everywhere GitHub deposunun yayınlar sayfasından [t-CLC ' nin en son sürümünü indirin](https://github.com/Microsoft/team-explorer-everywhere/releases) (örneğin, tee-CLC-14.134.0. zip bu yazma sırasında).
1. . Zip içeriğini diskteki bir klasöre ayıklayın.
1. MacOS Terminal uygulamasını açın ve önceki adımda kullandığınız klasöre geçmek için `cd` komutunu kullanın.
1. Komut satırı istemcisinin çalıştıracağınızı sınamak için klasörü içinden komut `./tf` çalıştırın, Java veya başka bağımlılıklar yüklemek isteyip istemediğiniz sorulabilir.

T-CLC yüklendikten sonra, istemcinin lisans sözleşmesini görüntülemek ve kabul etmek için `tf eula` komutunu çalıştırabilirsiniz.

Son olarak, TFS/Azure DevOps ortamınızdan kimlik doğrulamak için sunucuda bir kişisel erişim belirteci oluşturmanız gerekir. [Kişisel erişim belirteçleriyle kimlik doğrulama](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)hakkında daha fazla bilgi edinin. TFVC ile kullanmak için bir kişisel erişim belirteci oluştururken, belirteci yapılandırırken tam erişim sağladığınızdan emin olun.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Depoya bağlanmak için t-CLC kullanma

Kaynak kodunuza bağlanmak için öncelikle `tf workspace` komutunu kullanarak bir çalışma alanı oluşturmanız gerekir. Örneğin, aşağıdaki komutlar "Myorganleştirme" adlı Azure DevOps Services bir kuruluşa bağlanır: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS` ortamı ayarı, kimlik bilgilerinizi birden çok kez girmeniz istenmeyecek şekilde kaydetmek için kullanılır. Bir Kullanıcı adı sorulduğunda, önceki bölümde oluşturduğunuz kişisel erişim belirtecini kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızın bir yerel klasöre eşlenmesinin oluşturulması için `tf workfold` komutunu kullanırsınız. Aşağıdaki örnekte "WebApp. Services" adlı bir klasör "MyRepository" TFVC projesinden eşlenir ve yerel ~/Projects/klasörüne (yani geçerli kullanıcıların giriş klasöründeki "projeler" klasörü) kopyalanmak üzere ayarlanır.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanın:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>T-CLC kullanarak değişiklikler yürütülüyor

Mac için Visual Studio dosyalarınızda değişiklikler yaptıktan sonra, düzenlemelerinizi denetlemek için terminale geri dönebilirsiniz. `tf add` komutu, iade edilecek bekleyen değişiklikler listesine dosya eklemek için kullanılır ve `tf checkin` komutu sunucuda gerçek iade işlemini gerçekleştirir. `checkin` komutu, bir yorum eklemek veya ilgili bir iş öğesini ilişkilendirmek için parametreler içerir. Aşağıdaki kod parçacığında, bir `WebApp.Services` klasöründeki tüm dosyalar, iade etme için yinelemeli olarak eklenir. Ardından, kod bir yorum ile iade edilir ve "42" KIMLIĞINE sahip bir iş öğesiyle ilişkilendirilir.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada bahsedilen komutlar veya diğerleri hakkında daha fazla bilgi edinmek için terminalde aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Team Foundation Sürüm Denetimi uzantısını kullanarak TFVC 'ye bağlanma

> [!NOTE]
> MacOS üzerinde en iyi sürüm denetimi deneyimi için Team Foundation Sürüm Denetimi (TFVC) yerine git kullanmanız önerilir. Git Mac için Visual Studio desteklenir ve Team Foundation Server (TFS)/Azure DevOps içinde barındırılan depolar için varsayılan seçenektir. Git 'i TFS/Azure DevOps ile kullanma hakkında daha fazla bilgi edinmek için [Git deposu ayarlama](/visualstudio/mac/set-up-git-repository) makalesini inceleyin.
>
> Mac için Visual Studio için TFVC uzantısının önizleme sürümünü daha önce kullandıysanız, Mac için Visual Studio 2019 ' e yükseltirken artık bu desteklenmez.

Mac için Visual Studio uzantısı galerisinde, TFVC 'ye bağlanmak için sınırlı destek sunan bir Team Foundation sürüm denetimi uzantısı vardır. Uzantı desteklenmez ve bilinen birkaç soruna sahiptir, bu nedenle deneyiminiz kullanılırken farklılık gösterebilir.

Uzantıyı yüklemek için Mac için Visual Studio başlatın ve **Visual Studio > uzantıları** menüsünü seçin. **Galeri** SEKMESINDE, **TFS ve Azure DevOps için sürüm denetimi > Team Foundation sürüm denetimi** seçin ve ardından **Install...** ' a tıklayın:

![Uzantı Yöneticisi](media/tfvc-install.png)

Uzantıyı yüklemek için istemleri izleyin. Yüklendikten sonra IDE 'yi yeniden başlatın.

### <a name="updating-the-extension"></a>Uzantı güncelleştiriliyor

TFVC uzantılı güncelleştirmeler düzenli aralıklarla yapılır. Güncelleştirmelere erişmek için, menüden **Visual Studio > uzantıları...** öğesini seçin ve **güncelleştirmeler** sekmesini seçin. listede uzantıyı seçin ve **Güncelleştir** düğmesine basın:

Sonraki iletişim kutusunda **yükleme** ' ye basarak eski paketi kaldırın ve yenisini yükleme işlemini yapın.

### <a name="using-the-extension"></a>Uzantıyı kullanma

Uzantı yüklendikten sonra, **TFS/Azure DevOps > uzak depodan aç... menü öğesinden > sürüm denetimini** seçin.

![Uzantıyı açmak için menü öğesi](media/tfvc-source-control-explorer-devops.png)

Başlamak için VSTS veya Team Foundation Server seçin ve **devam**' a basın:

![Sunucu ile bağlanma](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos kimlik doğrulaması

Azure Repos barındırılan bir proje seçtiğinizde, Microsoft hesabı ayrıntılarını girmeniz istenir:

![Azure Repos bağlanma](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS kimlik doğrulaması

TFS 'ye bağlanmak için sunucu ayrıntılarını ve hesap kimlik bilgilerinizi girin. NTLM kimlik doğrulamasını kullanmak için bir etki alanı girin, aksi takdirde temel kimlik doğrulamasını kullanmak için boş bırakın. **Sunucu Ekle**' yi seçin:

![TFS sunucusunda oturum açma](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Proje seçme

Kimliği başarıyla doğrulandıktan sonra **kaynak denetiminden Aç** iletişim kutusundan hesapla ilişkili depoların bir listesini görebilirsiniz:

![Projeler görüntülenirken kaynak denetimi iletişim kutusundan Aç](media/tfvc-vsts-projects.png)

Bu iletişim kutusu aşağıdaki düğümlerle düzenlenmiştir:

- Azure DevOps organizasyonu veya koleksiyonu – bu, ile oturum açtığınız Microsoft hesabı bağlı tüm kuruluşları görüntüler.
- Projeler-her bir kuruluşta veya koleksiyonda bir dizi projeniz olabilir. Proje, kaynak kodu, iş öğeleri ve otomatikleştirilmiş derlemelerin barındırıldığı yerdir.

Bu noktada, bir proje veya kuruluş adına göre arama ve filtreleme yapabilirsiniz.

#### <a name="adding-a-new-server"></a>Yeni sunucu ekleme

Listeye yeni bir sunucu eklemek için, **kaynak denetiminden Aç** Iletişim kutusunda **konak Ekle** düğmesine basın:

![Listeye yeni sunucu eklemek için vurgulanan Ekle düğmesi](media/tfvc-add-new-server.png)

Listeden sağlayıcıyı seçin ve kimlik bilgilerinizi girin:

![Kaynak denetimi sağlayıcısı için seçeneği gösteren iletişim kutusu](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Yeni bir çalışma alanı oluşturma

Bir projeyle çalışmaya başlamak için bir _çalışma alanınız_olması gerekir. Zaten bir çalışma alanınız yoksa, **kaynak denetiminden Aç** Iletişim kutusunda **çalışma alanı** açılan kutusundan bir tane oluşturabilirsiniz:

![Yeni çalışma alanı oluştur ComboBox seçeneği](media/tfvc-create-new-workspace.png)

Yeni çalışma alanınız için ad ve yerel yolu ayarlayın ve **çalışma alanı oluştur**' u seçin:

![Yeni çalışma alanı için bir ad ve yerel yol girme](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Kaynak kodu Gezginini Kullanma

Bir çalışma alanı oluşturup projenizi eşleştirdikten sonra _kaynak kodu Gezgini_ile çalışmaya başlayabilirsiniz.

Kaynak kodu Gezginini açmak için, **sürüm denetimi > TFS/Azure DevOps > Kaynak Denetim Gezgini** menü öğesini seçin.

Kaynak kodu Gezgini, tüm eşlenmiş projeler, dosyaların ve klasörlerinin üzerinde gezinmenizi sağlar. Ayrıca, şu gibi tüm temel kaynak denetim eylemlerini gerçekleştirmenize olanak tanır:

- En son sürümü Al
- Belirli bir sürümü Al
- Dosyaları kullanıma alma ve iade etme
- Dosyaları kilitle ve kilidini aç
- Dosya ekleme, silme ve yeniden adlandırma
- Geçmişi görüntüle
- Değişiklikleri karşılaştırın.

Bu eylemlerin birçoğu projedeki bağlam eylemleri aracılığıyla kullanılabilir:

![Bir proje için bağlam menüsü eylemleri](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Çalışma alanlarını yönetme

[Çalışma alanı oluşturma](#creating-a-new-workspace) bölümünde açıklandığı gibi, zaten bir çalışma alanı oluşturmadıysanız, kaynak kodu Gezgini 'nin boş olduğunu fark edeceksiniz:

![Boş kaynak Kod Gezgini](media/tfvc-setup-empty-sce.png)

Uzak projenizi yerel bir çalışma alanı ile ayarlamak için aşağıdaki adımları kullanın:

1. ComboBox içinden **sunucuyu** seçin.
1. "Çalışma alanı yok" ve yerel yolun "Eşlenmedi" olduğunu unutmayın. **Yeni çalışma alanı oluştur** iletişim kutusunu göstermek için **eşlenmemiş** bağlantıyı seçin.
1. Çalışma alanı için bir ad girin ve ardından projeyi bilgisayarınızdaki yerel bir klasöre eşlemek için **çalışma klasörü Ekle** ' ye tıklayın:

    ![Varsayılan seçenekleri gösteren yeni bir çalışma alanı iletişim kutusu oluşturma](media/tfvc-workspace1.png)

1. Sunucunuzdaki tüm projeleri aynı çalışma alanına eşlemek için "$" klasörünü seçin ya da tek bir proje seçip **Tamam**' a tıklayın:

    ![Tüm projeleri gösteren klasör iletişim kutusu için tarama](media/tfvc-workspace2.png)

1. Yerel makinenizde proje (ler) i eşlemek istediğiniz konumu seçin ve **Klasör Seç**' e tıklayın.
1. **Tamam** 'a tıklayarak yeni çalışma alanının ayrıntılarını onaylayın

    ![Çalışma klasörüyle eklenen yeni çalışma alanı iletişim kutusu oluştur](media/tfvc-workspace3.png)

Çalışma alanınız kurulduktan sonra, kaynak kodu Gezgininde **çalışma alanlarını yönet** düğmesine tıklanarak değiştirilebilir veya kaldırılabilir.

![Çalışma alanlarını yönet](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Sorun Giderme ve Bilinen Sorunlar

#### <a name="problems-using-basic-authentication"></a>Temel kimlik doğrulaması kullanan sorunlar

Bir sunucu ile kimlik doğrulamak için aşağıdaki seçenekler kullanılabilir:

- OAuth
- Temel
- NT

Temel kimlik doğrulamasını kullanmak için aşağıdaki adımları izleyerek Azure DevOps Services **alternatif kimlik doğrulama kimlik bilgilerini** etkinleştirmek gerekir:

1. Azure DevOps kuruluşunuzda sahip olarak oturum açın (https:\//dev.Azure.com/{Organization}/{Project}).

2. Kuruluş araç çubuğunuzda dişli simgesini seçin ve **ilke**' yi seçin:

    ![İlke ayarları seçeneği seçildi](media/tfvc-auth2.png)

3. Uygulama bağlantı ayarlarınızı gözden geçirin. Güvenlik ilkelerinize bağlı olarak bu ayarları değiştirin:

    ![İlke ayarları seçeneği seçildi](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>TFVC 'de hiçbir şey görmüyorum

Geliştirme makinenizde Team Foundation Sürüm Denetimi (TFVC) ayarlamak için, çalışma [alanlarını yönetme](#managing-workspaces) bölümünde açıklandığı gibi bir çalışma alanı oluşturmanız **gerekir** .

Kaynak Denetim Gezgini, **çalışma alanlarını yönet** düğmesine basın. Projeyi geliştirme makinenizdeki bir klasöre eşlemek için adımları izleyin.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Projelerimin hiçbirini/tümünü göremiyorum

Kimlik doğrulamasından sonra proje listesini görmeniz gerekir. Varsayılan olarak, yalnızca TFS projeleri gösterilir. Diğer proje türlerini görmek için "tüm projeleri gör" kutusunu işaretleyin.

Doğru ayrıcalıklarınız yoksa, sunucuda bulunan projelerin görünmeyeceğini aklınızda bulundurun.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>"Çalışma alanı oluşturulamıyor" hatasını alıyorum. Lütfen yeniden deneyin "

[Yeni bir çalışma alanı oluşturmaya](#creating-a-new-workspace)çalışırken aşağıdaki koşulların karşılandığından emin olmanız gerekir:

- Çalışma alanı adında geçersiz karakter kullanımı.
- Ad 64 karakterden az olmalıdır.
- Yerel yol başka bir çalışma alanı tarafından kullanılamaz.

### <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kullanarak (Windows 'da) kodunuzu TFVC 'de geliştirme ve paylaşma](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)