---
title: 'Nasıl yapılır: katılımsız yükleme oluşturma ve çalıştırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833473"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Nasıl Yapılır: Katılımsız Visual Studio Yüklemesi Oluşturma ve Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yükleme uygulamasını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DVD gibi medya yerine bir intranet üzerinden katılımsız (yani özelleştirilmiş bir sessiz) yükleme olarak çalıştırabilirsiniz. Bu konu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir ağ paylaşımından bu yükleme türü için nasıl hazırlanılacağını açıklamaktadır.

## <a name="creating-a-network-image"></a>Ağ görüntüsü oluşturma
 İlk olarak, medyanın ağ görüntüsünü oluşturun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-create-a-network-image"></a>Bir ağ görüntüsü oluşturmak için

1. Sunucuda bir klasör oluşturun (örneğin, *sürücü*: \ IDEinstall \\ ).

2. Yükleyiciyi [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)adresinden indirin ve ardından *Product*. exe/Layout *Drive*: \ıdeınstall\ ' i çalıştırın.

3. Ağ üzerinde IDEinstall klasörünü paylaşma ve ardından uygun güvenlik ayarlarını belirleme.

     Yükleme uygulamasının ağ yolu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] \\ \\ *ServerName*\ ıdeınstall \\ *Product*. exe ' dir.

    > [!NOTE]
    > Herhangi bir yol ve dosya adı birleşimi 260 karakteri aşarsa, yükleme başarısız olabilir. İçindeki bir yolun en fazla uzunluğu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 221 karakterdir.  Yerel yol adı 70 karakteri aşmamalıdır ve ağ yolu adı 39 karakteri aşmamalıdır.

     Ayrıca, yoldaki klasör adları katıştırılmış boşluklar içeriyorsa (örneğin, " \\ \\ *ServerName*\ IDE install" veya \\ \\ *ServerName*\Adim Studio \\ ), yükleme başarısız olabilir.

## <a name="deploying-visual-studio-in-unattended-mode"></a>Visual Studio 'Yu katılımsız modda dağıtma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Katılımsız modda dağıtmak için AdminDeployment.xml dosyasını değiştirmeniz gerekir. Bunu yapmak için, önce `/CreateAdminFile` komut satırı parametresini kullanarak AdminDeployment.xml dosyasını oluşturmanız gerekir *\<file location>* . Daha sonra, bu dosyayı, bir Visual Studio dağıtımını ağınıza göndermek veya dosyayı *sürücü*: \ıdeınstall\packages dizinine yerleştirirseniz bir yüklemeye çekmek için kullanabilirsiniz. AdminDeployment.xml dosyası bir işletim sistemi, mimari, Visual Studio sürümü veya işletim sistemi dili için benzersiz değildir.

> [!CAUTION]
> Bazen AdminDeployment.xml dosyasında seçili olarak listelenen öğeler yüklenmez. Bu sorunu çözmek için, "Selected =" Yes "" olarak işaretlenmiş öğeleri AdminDeployment.xml dosyasının **sonuna** yerleştirin.
>
> Bir öğenin isteğe bağlı bağımlılıklarını yüklemek istemiyorsanız, önce üst öğeyi seçmeli ve sonra aşağıdaki ekran görüntüsünde gösterildiği gibi üst öğeden sonra isteğe bağlı bağımlılıkların seçimini kaldırmanız gerekir:
>
> ![AdminDeployment.xml dosyasının sonundaki yükleme öğeleri](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> Bunu yapmanın bir başka yolu da bir üst öğenin isteğe bağlı alt öğelerini atmaktır. başka bir deyişle, "Selected =" No "" öğelerini eklemeyin, ancak yine de AdminDeployment.xml dosyanın sonundaki "Selected =" Yes "" öğelerini yerleştirmeniz gerekir.

> [!IMPORTANT]
> Yükleme sırasında, bilgisayar bir veya daha fazla kez otomatik olarak yeniden başlatılabilir. Yeniden başlatıldıktan sonra, bilgisayar yeniden başlatılmadan önce yüklemeyi gerçekleştirmek üzere oturum açtığınız kullanıcı hesabıyla yeniden oturum açmanız gerekir. Katılımsız yüklemeyi çalıştırmadan önce önkoşul bileşenlerini yükleyerek otomatik yeniden başlatmalara engel olabilirsiniz. Daha fazla bilgi için [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)'Ndaki "Kurulum sırasında yeniden başlatmayı önleyin" başlıklı bölüme bakın.

 AdminDeployment dosya şeması, aşağıdaki öğeleri içerir:

|Öğe|Öznitelik|Değerler|Açıklama|
|-------------|---------------|------------|-----------------|
|Paketleme Liözelleştirmeler|Dır|*Yol*|Yükleme uygulamasının Kullanıcı arabirimindeki yolu geçersiz kılma ile aynı şekilde davranır. Bu öğe, Visual Studio zaten yüklüyse yoksayılır.|
|Paketleme Liözelleştirmeler|NoWeb|Evet&#124;varsayılan|Bu öğenin değeri Evet ise, yükleme uygulaması kurulum eylemi sırasında hiçbir şekilde Web 'e gitmeye çalışır.|
|SelectableItemCustomization|Gizli|Evet&#124;Hayır|Bu öğenin değeri Evet ise, özelleştirme ağacındaki seçilebilir bir öğeyi gizler.|
|SelectableItemCustomization|Seçili|Evet&#124;Hayır|Özelleştirme ağacındaki seçilebilir bir öğeyi seçer veya temizler.|
|Paketleme Liözelleştirmeler|Akış|Yol|Kullanıcının kullanmak istediği akışın konumu.  Bu akış, makinedeki sonraki değiştirme işlemleri için (varsayılan olarak "varsayılan") kullanılır.|
|Paketleme Liözelleştirmeler|SuppressRefreshPrompt|Evet&#124;varsayılan|, Daha yeni bir tane varsa, kullanıcının kurulum 'u yenilemesini engellemesine engel olur.|
|Paketleme Liözelleştirmeler|NoRefresh|Evet&#124;varsayılan|Yeni bir tane varsa kurulum yenilemez.|
|Paketleme Liözelleştirmeler|NoCacheOnlyMode|Evet&#124;varsayılan|Paket önbelleğinin önceden doldurulmasını engeller.|

> [!WARNING]
> Yükleme uygulaması, gizlenmiş olsa bile SelectableItem 'ın seçili durumuna göre belirlenir. Örneğin, her zaman seçilebilir bir öğeyi yüklemek istiyorsanız, onu gizli ve seçili olarak işaretleyebilirsiniz.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Visual Studio 'nun katılımsız bir yüklemesini oluşturmak için

1. *Sürücü*:\IDEinstall\AdminDeployment.xml dosyası ' nda, aşağıdaki örnekte gösterildiği gibi, paketleme Licustomizations öğesinin NoWeb özniteliğinin değerini "default" iken "Yes" olarak değiştirin:

     Değiştir `<BundleCustomizations TargetDir="default" NoWeb="default"/>``<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. SelectableItemCustomization özniteliğini isteğe bağlı bileşenler için gereken şekilde değiştirin ve dosyayı kaydedin.

## <a name="running-unattended-setup"></a>Katılımsız kurulum çalıştırma
 Katılımsız kurulum 'u, istemci bilgisayarlarda Visual Studio için yükleme uygulamasını otomatik olarak çalıştırarak veya kullanıcıların sizin tanımladığınız ayarları kullanarak uygulamayı kendi kendilerine çalıştırmasına izin vererek çalıştırabilirsiniz.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>İstemci bilgisayarda katılımsız yükleme çalıştırmak için

- **Başlat** menüsünü açın, **Çalıştır**' ı seçin ve sonra \\ \\ *sunucuadı*\ ıdeınstall\ vs_*Product*. exe/adminfile *PathOfTheAdmindeployment.xmldosya*<em>additionalparametersasgerekli</em> yazın

   Örneğin, aşağıdaki komut satırını belirtebilirsiniz: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>İstemcilerin Visual Studio 'Yu önceden tanımlı ayarlarla el ile yüklemesini sağlamak için

1. Özelleştirilmiş AdminDeployment.xml dosyasını salt okunurdur olan bir ağ paylaşımının içine kopyalayın (örneğin, \\ \\ *ServerName*\IDEinstall\packages\AdminDeployment.xml).

2. Kullanıcıların söz konusu paylaşımdan yüklemesini sağlar.

## <a name="maintaining-an-installation"></a>Yükleme sürdürme
 **Denetim Masası** 'nı açıp yükleme uygulamasını yeniden çalıştırırsanız, Visual Studio 'nun özelliklerini değiştirebilir, programlama dillerini kaldırabilir ve Visual Studio 'yu onarabilir veya kaldırabilirsiniz.

> [!NOTE]
> Bakım modunu kullanmak için yerel bilgisayarda yönetici kimlik bilgilerine sahip olmanız gerekir.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>İstemci bilgisayarda yükleme sürdürmek için

- **Denetim Masası**' nı açın ve ardından **Programlar ve Özellikler**' i seçin.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Öğesini seçin ve ardından **Değiştir**' i seçin.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>İstemci bilgisayardaki AdminDeployment ayarlarını, Visual Studio yüklendikten sonra değiştirmek için

1. AdminDeployment.xml gerektiği şekilde güncelleştirin.

2. **Başlat** menüsünü açın ve **Çalıştır**' ı seçin.

3. Şu metni girin: \\ \\ *ServerName*\ideınstall\ vs_*Product*. exe/adminfile PathToAdmindeployment.xml dosyası

    Additionalparametersasgerekli

    Örneğin, aşağıdaki komut satırını belirtebilirsiniz: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Visual Studio yüklendikten sonra varsayılan parametre onarım ' dır. Visual Studio 'Yu güncelleştirilmiş bir/AdminFile ile onarırsanız, güncel Yönetici dağıtım ayarlarını, güncelleştirilmiş AdminDeployment.xml dosyasının çağıranlarla birlikte geçersiz kılacaksınız.

## <a name="updating-an-installation"></a>Yükleme güncelleştiriliyor
 Microsoft, Visual Studio 2015 için birkaç güncelleştirme yayımlamıştır. Bu bölümde, güncelleştirmeleri içermesi için Visual Studio 2015 ' nin katılımsız yükleme görüntünüzü güncelleştirme işlemleri açıklanmaktadır.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Visual Studio 'nun katılımsız bir yüklemesini güncelleştirmek için

1. Mevcut ağ görüntüsündeki Product.exe dosyasını bulun, sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Ayrıntılar** sekmesine tıklayın ve ardından **ürün sürümü** özelliğini aklınızda olun.

    ![Visual Studio 'nun katılımsız yüklemesinde Özellikler iletişim kutusu örneği](../install/media/unattended-install-properties-dialog-box.PNG "Katılımsız kurulum-Özellikler Iletişim kutusu")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Ürün sürümü 14.0.24720.0 veya 14.0.24720.1 ise, şu adımları izleyin:
   1. Internet erişimi olan bir makineye *Product.exe* /Layout *Drive:* \ıdeınstall komutunu çalıştırın. (Örneğin, şunu çalıştırın: `vs_enterprise.exe /Layout d:\IDEinstall` .)

   2. /Layout tamamlandıktan sonra yeni görüntüyü yeni bir konuma kopyalayın.

   3. AdminDeployment.xml dosyasını oluşturun ve değiştirin. Bunu yapmak için `/CreateAdminFile` *\<file location>* komut satırı parametresini kullanın. (Daha fazla bilgi için, bu makalenin "Visual Studio 'Yu katılımsız modda dağıtma" bölümüne bakın.)

   4. İstemci makinede, daha önce yüklediğiniz Visual Studio kopyasını güncelleştirmek için aşağıdaki komutu çalıştırın: " \\ \\ *Sunucu1*\ IDEinstall_Updated_1 \\ *Product.exe* /adminfile \ \\ sunucu1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart".

        Örneğin şunu çalıştırın: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Diğer ürün sürümü değerleri için şu adımları izleyin:
   1. Internet erişimi olan bir makineye *Product.exe* /Layout *Drive:* \ıdeınstall komutunu çalıştırın. (Örneğin, öğesini çalıştırın `vs-enterprise.exe /Layout d:\IDEinstall` .)

   2. /Layout tamamlandıktan sonra yeni görüntüyü yeni bir konuma kopyalayın. (Veya bunun yerine var olan ağ görüntüsünü geçersiz kılabilirsiniz.)

   3. AdminDeployment.xml dosyasını oluşturun ve değiştirin. Bunu yapmak için `/CreateAdminFile` *\<file location>* komut satırı parametresini kullanın. (Daha fazla bilgi için, bu makalenin "Visual Studio 'Yu katılımsız modda dağıtma" bölümüne bakın.)

   4. Görüntüyü yeni bir konuma kopyalarsanız, daha önce yüklediğiniz Visual Studio 'nun kopyasını güncelleştirmek için istemci makinesinde şu komutu çalıştırmanız gerekir: " \\ \\ *Sunucu1*\ IDEinstall_Updated_1 \\ *Product.exe* /adminfile \ \\ sunucu1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart".

        Örneğin şunu çalıştırın: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. Var olan ağ görüntüsünü geçersiz kılarsınız, önceki adımda listelendiği gibi komutu çalıştırabilirsiniz veya şunları yapabilirsiniz:
       1. **Denetim Masası**' nı açın ve ardından **Programlar ve Özellikler**' i seçin.

       2. **Visual Studio**' yı ve ardından **Değiştir**' i seçin.

       3. Visual Studio bakım modunda başladıktan sonra **Değiştir**' e tıklayın.

       4. En son güncelleştirme Özellikler sayfasında görünmelidir. Yüklemek istediğiniz diğer özellikleri seçin, **İleri**' ye tıklayın ve **ardından Güncelleştir ' e tıklayarak** güncelleştirme ve yeni özellikleri yükleyebilirsiniz.

## <a name="registering-the-product"></a>Ürün kaydediliyor
 Yükleme tamamlandıktan sonra, içinden kopyanızı kaydedebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-register"></a>Kaydolmak için

1. **Yardım** menüsünü açın ve **ürünü kaydet**' i seçin.

2. Ürün anahtarını girin.

     (Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio ürün anahtarını bulma](../install/how-to-locate-the-visual-studio-product-key.md) ve [nasıl yapılır: Visual Studio 'yu dağıtmaya yönelik ürün anahtarlarını otomatik olarak uygulama](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) konuları.)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'yu yükleme](../install/install-visual-studio-2015.md)