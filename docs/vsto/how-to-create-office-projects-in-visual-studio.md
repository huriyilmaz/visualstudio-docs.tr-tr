---
title: 'Nasıl Office: Office projelerini Visual Studio'
description: Visual Studio uygulamaları için VSTO ve belge düzeyinde özelleştirmeler oluşturmak için Microsoft Office öğrenin.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7bb09eda68dac56d76bc3fee09b14b9a03fca147
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972251"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Nasıl Office: Office projelerini Visual Studio
  Uygulama uygulamaları için VSTO ve belge düzeyinde özelleştirmeler oluşturmak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için Microsoft Office kullanabilirsiniz. Bu tür projeler hakkında daha fazla bilgi için bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>Bir eklenti VSTO oluşturmak için

1. Dosya menüsünde **Yeni** **dosya'Project.**  >   Tümleşik geliştirme ortamınız (IDE) geliştirme ayarlarını kullanmak üzere ayarlanmışsa Dosya menüsünde Yeni [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]    >  **uygulama'Project.**

    **Yeni Proje** iletişim kutusu görünür.

   > [!NOTE]
   > Office varsayılan olarak [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] hedefini kullanır. Daha fazla bilgi için [bkz. .NET Framework profili.](/dotnet/framework/deployment/client-profile)

2. Şablonlar bölmesinde, kullanmak istediğiniz dilin düğümünün altında, **Office/SharePoint.**

3. Yeni **Office düğümünü** seçin.

4. Proje şablonları listesinde, Bir VSTO proje şablonu seçin. Eklenti proje şablonları için VSTO listesi için bkz. [Office proje şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

   > [!NOTE]
   > **Office** Eklentileri düğümünü seçerek proje şablonları görünmüyorsa, iletişim kutusunun üst kısmında yer alan birleşik giriş kutusunda **.NET Framework 4** veya daha yeni bir değer seçildiğinden emin olun. Office proje şablonları her iki sürüm için de .NET Framework.

5. Ad **kutusuna** proje için bir ad yazın. Varsayılan olarak, çözüm adı olarak proje adı da kullanılır.

6. Konum **kutusuna** projeyi oluşturmak istediğiniz yolu girin. Mutlak ve evrensel adlandırma kuralı (UNC) yollarını kullanabilirsiniz. HTTP, FTP veya diğer protokol yollarını kullanmayın.

    Konumlar aşağıdaki biçimlere sahiptir:

   * [*sürücü*\]\:

   * \\\\*Sunucu* \\ *Paylaş*

     Konumda şu karakterleri kullanmayın:

   * Yıldız işareti (*)

   * Dikey çubuk (|)

   * İki nokta (:) (Sürücü harfini takip eden hariç.)

   * Çift tırnak işareti (") (Boşluk içeren yolların tırnak işaretine ihtiyacı olmaz.)

   * Küçük ( \< )

   * Büyüktür (>)

   * Soru işareti (?)

   * Yüzde işareti (%)

7. Tamam **düğmesini** seçin.

   ::: moniker range="vs-2017"

   > [!NOTE]
   > Eklenti projeleri oluşturulduğunda her zaman kaydedilir. Bunlar geçici projeler olarak oluşturulamaz. Geçici projeler hakkında daha fazla bilgi için bkz. [Geçici projeler.](../ide/creating-solutions-and-projects.md#create-a-temporary-project)

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>Belge düzeyi özelleştirme projesi oluşturmak için

1. Dosya menüsünde **Yeni** **dosya'Project.**  >   IDE'niz geliştirme ayarlarını Visual Basic olarak ayarlanmışsa  Dosya menüsünde Yeni **uygulama'Project.**  >  

    **Yeni Proje** iletişim kutusu görünür.

2. Şablonlar bölmesinde, kullanmak istediğiniz dilin düğümünün altında, **Office/SharePoint.**

3. Yeni **Office düğümünü** seçin.

4. Proje şablonları listesinde bir belge düzeyi proje şablonu seçin. Kullanılabilir belge düzeyi proje şablonlarının listesi için bkz. [Office proje şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

   > [!NOTE]
   > Office **Add-ins** düğümünü .NET Framework proje şablonları **görünmüyorsa, 4** veya .NET Framework seçildiğinden emin olun.

5. Ad **kutusuna** proje için bir ad yazın. Varsayılan olarak, bu ad belge için de kullanılır. IDE'niz Visual C# geliştirme ayarlarını veya Genel geliştirme ayarlarını kullanmak üzere ayarlanmışsa bir konum ve çözüm adı da girin.

   > [!NOTE]
   > Proje konumunun yolunda veya proje adı içinde vekil karakterler kullanılamaz. Ayrıca, çözümü çevrimdışı kullanmak üzere dağıtmayı planlıyorsanız, proje adı karakterleriNIN HTTP protokolü belirtimleri ile aynı olması gerekir.

6. Tamam **düğmesini** seçin.

    Office için Visual Studio Araçları Project **Sihirbazı** açılır.

7. Çözüm **için yeni bir belge** oluşturmak için Yeni belge oluştur'a veya var olan bir belgeyi özelleştirmek için Var olan bir belgeyi kopyala'ya tıklayın'ı seçin. 

    Yeni bir belge ekleyebilirsiniz, Ad  kutusunda adı belirtin ve Biçim kutusunu kullanarak belgenin **biçimini** seçin. Kullanılabilir biçimler hakkında daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerin mimarisi.](../vsto/architecture-of-document-level-customizations.md)

    Mevcut bir belgeyi kullanıyorsanız, belgenin konumunu mevcut belge **kutusunun Tam yolunda** belirtin. Mutlak ve UNC yollarını kullanabilirsiniz. Belge için HTTP, FTP veya diğer protokol yollarını kullanmayın.

    Konumlar aşağıdaki biçimlere sahiptir:

   - [*sürücü*\]\:

   - \\\\*Sunucu* \\ *Paylaş*

     Konumda şu karakterleri kullanmayın:

   - Yıldız işareti (*)

   - Dikey çubuk (|)

   - İki nokta (:) (Sürücü harfini takip eden hariç.)

   - Çift tırnak işareti (") (Boşluk içeren yolların tırnak işaretine ihtiyacı olmaz.)

   - Küçük ( \< )

   - Büyüktür (>)

   - Soru işareti (?)

   - Yüzde işareti (%)

   > [!NOTE]
   > Bir projede mevcut bir belgeyi [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] kullanıyorsanız, yalnızca içinde oluşturulan veya 'ye dönüştürülen belgeleri [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] kullanın. Benzer şekilde, bir Word 2010 projesinde mevcut bir belgeyi kullanıyorsanız, yalnızca içinde oluşturulmuş veya Word 2010'a dönüştürülmüş belgeleri kullanın. Word'un önceki bir sürümünde oluşturulmuş bir belge kullanırsanız, belgede bazı özellikler devre dışı bırakılır. Bu özellikleri kullanan bir kod yazmayı denersiniz, projeniz hatalarla karşılaşabilirsiniz. Bir belgeyi dönüştürmek için veya [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] Word 2010'da açın, şeritteki Dosya sekmesinde Bilgi **Dönüştürme'yi**   >  **seçin.**

8. **Son**’u seçin.

9. Aşağıdaki durumlarda proje klasörünü ve alt klasörlerini Word'de Güven Merkezi'nde güvenilen konumlar listesine ekleyin:

   - Bir *.docm* dosyasını temel alan bir Word Belgesi oluşturuyorsanız ve belge bir VBA projesi veya Windows Forms denetimlerini barındırır. Proje klasörünü güvenilen konumlar listesine eklemek, belgenin tasarım zamanında beklendiği gibi çalışmanıza yardımcı olur.

   - *.dotx* dosyasını temel alan bir Word Şablonu projesi oluşturuyorsanız. Projeyi çalıştırarak hata ayıklamak için proje klasörünü güvenilen konumlar listesine eklemeniz gerekir.

     Güvenilen konumlara belge ekleme hakkında daha fazla bilgi için, Microsoft Office Online web sitesi Dosyalarınız için güvenilir bir konum oluşturma, kaldırma [veya değiştirme belgesine bakın.](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)

## <a name="see-also"></a>Ayrıca bkz.
- [Office şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [İşbirlikçi Office geliştirme](../vsto/collaborative-development-of-office-solutions.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)
