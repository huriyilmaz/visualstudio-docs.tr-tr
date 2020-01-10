---
title: Özel Modelleme Araç kutusu öğesi tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a038150519ea7a40a52fb1be16ed93045c09eed
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851515"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Özel bir modelleme araç kutusu öğesi tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sık kullandığınız bir modele göre öğe veya öğe grubu oluşturmayı kolaylaştırmak için, Visual Studio 'daki Modelleme diyagramlarının araç kutusuna yeni araçlar ekleyebilirsiniz. Bu araç kutusu öğelerini diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Özel bir araç diyagramda bir veya daha fazla yeni öğe oluşturur. Örneğin, aşağıdaki gibi öğeler oluşturmak için özel bir araç yapabilirsiniz:

- .NET profiline bağlı bir paket ve .NET stereotipine sahip bir sınıf.

- Gözlemci modelini temsil eden bir ilişki tarafından bağlanmış bir sınıf çifti.

> [!NOTE]
> Bu yöntemi, öğe araçları oluşturmak için kullanabilirsiniz. Diğer bir deyişle, araç kutusundan bir diyagram üzerine sürüklediğiniz araçlar oluşturabilirsiniz. Bağlayıcı Araçları oluşturamazsınız.

## <a name="DefineTool"></a>Özel Modelleme aracı tanımlama

#### <a name="to-define-a-custom-modeling-tool"></a>Özel bir modelleme aracı tanımlamak için

1. Öğe veya öğe grubunu içeren bir UML diyagramı oluşturun.

    - Bu öğelerin aralarında ilişki olabilir ve bağlantı noktaları, öznitelikler, işlemler veya PIN 'ler gibi yan alt öğeleri olabilir.

2. Yeni araca vermek istediğiniz adı kullanarak Diyagramı kaydedin. **Dosya** menüsünde Kaydet ' i kullanın **... As**.

3. Windows Gezgini 'ni kullanarak, iki diyagram dosyasını aşağıdaki klasöre veya herhangi bir alt klasöre kopyalayın:

     *Yourbelgelerimiz* **\Adim Studio\architecture Tools\custom araç kutusu öğeleri**

    - Zaten mevcut değilse bu klasörü oluşturun. Hem **mimari araçları** hem de **özel araç kutusu öğeleri**oluşturmanız gerekebilir.

    - Her iki diyagram dosyasını da bir adı "... **".** ..... **Diagram. Layout**"

    - İstediğiniz kadar özel araç yapabilirsiniz. Her araç için bir diyagram kullanın.

4. Seçim [Özel araçların özelliklerini tanımlama](#tbxinfo)başlığı altında açıklandığı gibi bir **. tbxinfo** dosyası oluşturun ve aynı dizine ekleyin. Bu, araç kutusu simgesini, araç ipucunu ve benzerlerini tanımlamanızı sağlar.

    - Tek bir **. tbxinfo** dosyası, çeşitli araçları tanımlamak için kullanılabilir. Bu, alt klasörlerdeki diyagram dosyalarına başvurabilir.

5. Visual Studio'yu yeniden başlatın. Ek araç, uygun diyagram türü için araç kutusunda görünür.

### <a name="what-the-custom-tool-will-replicate"></a>Özel aracın çoğaltılacağı
 Özel bir araç, kaynak diyagramın özelliklerinin çoğunu çoğaltacaktır:

- Adlardan. Araç kutusundan bir öğe oluşturulduğunda, aynı ad alanında yinelenen adların olmaması için gerekirse adın sonuna bir sayı eklenir.

- Renkler, Boyutlar ve şekiller

- Stereotipler ve paket profilleri

- Gibi özellik değerleri soyut

- Bağlantılı iş öğeleri

- Çoğullılıklar ve ilişkilerin diğer özellikleri

- Şekillerin göreli konumları.

  Aşağıdaki özellikler özel bir araçta korunmaz:

- Basit şekiller. Bunlar, model öğeleriyle ilgili olmayan şekillerdir, bu da bazı tür diyagramlarda çizim yapabilirsiniz.

- Bağlayıcı yönlendirme. Bağlayıcıları el ile yönlendirdiğinizde, aracınız kullanıldığında yönlendirme korunmaz. Bağlantı noktaları gibi bazı iç içe şekillerin konumları sahiplerine göre korunmaz.

## <a name="tbxinfo"></a>Özel araçların özelliklerini tanımlama
 Bir araç kutusu bilgi ( **. tbxinfo**) dosyası, bir veya daha fazla özel araç için bir araç kutusu adı, simge, araç ipucu, sekme ve Yardım anahtar sözcüğü belirtmenize olanak tanır. Bunu, **MyTools. tbxinfo**gibi bir ad verin.

 Dosyanın genel formu aşağıdaki gibidir:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Her öğenin değeri şunlardan biri olabilir:

- Örnekte gösterildiği gibi, araç kutusu simgesi için `<bmp fileName="…"/>` ve diğer öğeler için `<value>string</value>`.

  \- veya -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   Bu durumda, dize değerlerinin kaynak olarak derlendiği derlenmiş bir derleme sağlarsınız.

  Tanımlamak istediğiniz her araç kutusu öğesi için bir `<customToolboxItem>` düğümü ekleyin.

  **. Tbxinfo** dosyasındaki düğümler aşağıdaki gibidir. Her düğüm için varsayılan bir değer vardır.

|Düğüm adı|Tanımlar|
|---------------|-------------|
|displayName|Araç kutusu öğesinin adı.|
|tabName|Öğenin görünmesi gereken araç kutusu sekmesi. Bu tür diyagram için normal sekmenin adını ya da ayrı bir adı belirtebilirsiniz.|
|görüntü|Yüksekliği 16 ve 16 bit renk derinliğine sahip olması gereken bit eşlem ( **. bmp**) dosyasının konumu.|
|f1Keyword|Yardım konusunu bulan anahtar sözcük.|
|ipucuna|Bu araç için araç ipucu.|

 Bit eşlem dosyasını Visual Studio 'da düzenleyebilir ve Özellikler penceresi yüksekliğini ve genişliğini 16 olarak ayarlayabilirsiniz.

> [!NOTE]
> Diyagram dosyalarını kendi üzerinde kullanmaya çalıştıktan sonra bir. tbxinfo dosyası kullanmaya başladıysanız araç kutusu öğesinin hem eski hem de yeni sürümlerini içerdiğini görebilirsiniz. Bu durum, Diyagram dosyasının adı. tbxinfo dosyasında yanlış olursa da oluşabilir. Bu durumda, araç kutusunun kısayol menüsünde, **araç kutusunu Sıfırla**' yı seçin. Özel araç kutusu öğeleri kaybolur. Visual Studio 'Yu yeniden başlatın ve doğru özel öğeler görüntülenir.

## <a name="Extension"></a>Visual Studio uzantısında araç kutusu öğelerini dağıtma
 Araç kutusu öğelerini, bir Visual Studio uzantısı 'na (VSıX) paketleyerek diğer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanıcılara dağıtabilirsiniz. Komutları, profilleri ve diğer uzantıları aynı VSıX dosyasında paketleyebilir. Daha fazla bilgi için bkz. [Visual Studio uzantılarını dağıtma](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

 Visual Studio uzantısı oluşturmanın her zamanki yolu VSıX proje şablonunu kullanmaktır. Bunu yapmak için [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]yüklemiş olmanız gerekir.

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Visual Studio uzantısına bir araç kutusu öğesi eklemek için

1. [Bir veya daha fazla özel araç oluşturun ve test](#DefineTool)edin.

2. Araçlara başvuran [bir. tbxinfo dosyası oluşturun](#tbxinfo) .

3. Mevcut bir Visual Studio uzantısı projesi açın.

     \- veya -

     Yeni bir Visual Studio uzantısı projesi tanımlayın.

    1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

    2. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**' ın altında, **görsel C#** , **genişletilebilirlik**, **VSIX projesi**' ni seçin.

4. Araç kutusu tanımlarınızı projeye ekleyin. **. Tbxinfo** dosyasını, diyagram dosyalarını, bit eşlem dosyalarını ve herhangi bir kaynak dosyasını dahil edın ve VSIX 'e dahil olduklarından emin olun.

    - Çözüm Gezgini, VSıX projesinin kısayol menüsünde, **Ekle**, **Varolan öğe**' yi seçin. İletişim kutusunda, şu **tür nesneleri ayarlayın: tüm dosyalar**. Dosyaları bulun, tümünü seçin ve ardından **Ekle**' yi seçin.

        > [!NOTE]
        > Bu projede, model düzenleyicisinde diyagram dosyalarını açamazsınız.

5. Az önce eklediğiniz tüm dosyaların aşağıdaki özelliklerini ayarlayın. Özelliklerini, Çözüm Gezgini ' de tümünü seçerek aynı anda ayarlayabilirsiniz. Projedeki diğer dosyaların özelliklerini değiştirmemeye dikkat edin.

     **Her zaman kopyala** = **Çıkış Dizinine Kopyala**

     **Derleme Eylemi** = **İçerik**

     VSıX = **true** **olarak ekle**

6. Açık **kaynak. Extension. valtmanifest**. Uzantı bildirim düzenleyicisinde açılır.

7. **Meta veriler**altında özel araçlar için bir açıklama ekleyin.

     **Varlıklar**' ın altında, **Yeni** ' yi seçin ve iletişim kutusundaki alanları aşağıdaki gibi ayarlayın:

    -  = **özel uzantı türü** **yazın**

    - Tür = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Bu, açılan listedeki seçeneklerden biri değildir. Klavyeyi kullanarak girmeniz gerekir.

    - **Dosya sisteminde** **kaynak** = dosyası.

    - **Path** = **. tbxinfo** dosyanız, örneğin **MyTools. tbxinfo**

8. Projeyi oluşturun.

9. **Uzantının çalıştığını doğrulamak Için**F5 ' e basın. Visual Studio 'nun deneysel örneği başlar.

     Deneysel örnekte, ilgili türün UML diyagramını oluşturun veya açın. Yeni araclarınızın araç kutusunda göründüğünü ve öğe doğru bir şekilde oluşturduğunu doğrulayın.

10. **Dağıtım için BIR VSIX dosyası almak için:** Windows Gezgini 'nde, **. vsix** dosyasını bulmak için, **\ \Bin\debug** veya. **\bin\Release** klasörünü açın. Bu bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı dosyasıdır. Bu, bilgisayarınıza yüklenebilir ve diğer Visual Studio kullanıcılarına da gönderilebilir.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Visual Studio uzantısı 'ndan özel araçlar yüklemek için

1. `.vsix` dosyasını Windows Gezgini 'nde veya Visual Studio 'da açın.

2. Görüntülenen iletişim kutusunda, **Kur** ' ı seçin.

3. Uzantıyı kaldırmak veya geçici olarak devre dışı bırakmak için, **Araçlar** menüsünden **Uzantılar ve güncelleştirmeler** ' i açın.

## <a name="localization"></a>Yerelleştirme
 Başka bir bilgisayarda yüklü olduğunda, hedef bilgisayarın dilinde araç adlarını ve araç ipuçlarını görüntüleyen bir uzantı yapabilirsiniz.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Araç sürümlerini birden fazla dilde sağlamak için

1. Bir veya daha fazla özel araç içeren bir Visual Studio uzantısı projesi oluşturun.

    **. Tbxinfo** dosyasında, aracın `displayName`, araç kutusu `tabName`ve araç ipucunu tanımlamak için kaynak dosyası yöntemini kullanın. Bu dizelerin tanımlandığı bir kaynak dosyası oluşturun, bir derlemeye derleyin ve tbxinfo dosyasından başvurun.

2. Diğer dillerdeki dizeler ile kaynak dosyalarını içeren ek derlemeler oluşturun.

3. Her ek derlemeyi, adı dilin kültür kodu olan bir klasöre yerleştirin. Örneğin, derlemenin bir Fransızca sürümünü **fr**adlı bir klasörün içine yerleştirin.

4. `fr-CA`gibi belirli bir kültürün değil, genellikle iki harf olan bağımsız bir kültür kodu kullanmanız gerekir. Kültür kodları hakkında daha fazla bilgi için, kültür kodlarının tamamen bir listesini sağlayan [CultureInfo. Getkültürleri yöntemine](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx)bakın.

5. Visual Studio uzantısı oluşturun ve dağıtın.

6. Uzantı başka bir bilgisayara yüklendiğinde, kullanıcının yerel kültürüne ait kaynak dosyasının sürümü otomatik olarak yüklenir. Kullanıcının kültürü için bir sürüm sağlamadıysanız varsayılan kaynaklar kullanılacaktır.

   Prototip diyagramının farklı sürümlerini yüklemek için bu yöntemi kullanamazsınız. Öğelerin ve bağlayıcıların adları her yüklemede aynı olacaktır.

## <a name="other-toolbox-operations"></a>Diğer araç kutusu Işlemleri
 Genellikle, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]araç kutusunu, araçları yeniden adlandırarak, farklı araç kutusu sekmelerine taşıyarak ve bunları silerek kişiselleştirebilirsiniz. Ancak bu değişiklikler, bu konuda açıklanan yordamlarla oluşturulan özel modelleme araçları için kalıcı olmaz. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]yeniden başlattığınızda özel araçlar, tanımlı adları ve araç kutusu konumları ile yeniden görüntülenir.

 Ayrıca, **sıfırlama araç kutusu** komutunu gerçekleştirirseniz özel araçlarınız kaybolur. Ancak, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]yeniden başlattığınızda yeniden görüntülenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramları GENIŞLETME](../modeling/extend-uml-models-and-diagrams.md) [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md) [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [UML modelleri için doğrulama kısıtlamalarını tanımlama](../modeling/define-validation-constraints-for-uml-models.md)
