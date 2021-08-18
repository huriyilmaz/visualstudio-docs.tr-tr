---
title: 'nasıl yapılır: Visual Studio Office projeler oluşturma'
description: Microsoft Office uygulamaları için VSTO eklenti ve belge düzeyi özelleştirmeleri oluşturmak üzere Visual Studio nasıl kullanabileceğinizi öğrenin.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
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
ms.openlocfilehash: 126f4c88dd13ff9204ce2e29c2a95cf14df5d473
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046925"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>nasıl yapılır: Visual Studio Office projeler oluşturma
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Microsoft Office uygulamalar için VSTO eklentisi ve belge düzeyi özelleştirmeler oluşturmak için kullanabilirsiniz. bu proje türleri hakkında daha fazla bilgi için, bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>VSTO eklentisi projesi oluşturmak için

1. **dosya** menüsünde **yeni**  >  **Project**' yi seçin. tümleşik geliştirme ortamınız (ıde) geliştirme ayarlarını kullanacak şekilde ayarlandıysa [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

    **Yeni Proje** iletişim kutusu görünür.

   > [!NOTE]
   > Office projeleri [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] varsayılan olarak hedefleyin. daha fazla bilgi için bkz. [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile).

2. şablonlar bölmesinde, kullanmak istediğiniz dilin düğümü altında **Office/SharePoint**' ı genişletin.

3. **Office eklentileri** düğümünü seçin.

4. proje şablonları listesinde bir VSTO eklentisi proje şablonu seçin. kullanılabilir VSTO eklentisi proje şablonlarının listesi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > **Office eklentileri** düğümünü seçerken proje şablonları görünür değilse, iletişim kutusunun en üstündeki açılan kutuda **.NET Framework 4** veya sonraki bir sürümünün seçildiğinden emin olun. Office proje şablonları .NET Framework her iki sürümü için görülebilir.

5. **Ad** kutusuna proje için bir ad yazın. Varsayılan olarak, proje adı çözüm adı olarak da kullanılır.

6. **Konum** kutusunda, projeyi oluşturmak istediğiniz yolu girin. Mutlak ve evrensel adlandırma kuralı (UNC) yollarını kullanabilirsiniz. HTTP, FTP veya diğer protokol yollarını kullanmayın.

    Konumlar aşağıdaki biçimlere sahiptir:

   * [*sürücü*\]\:

   * \\\\*Sunucu* \\ *Paylaşma*

     Bu karakterleri konumda kullanmayın:

   * Yıldız işareti (*)

   * Dikey çubuk (|)

   * İki nokta (:) (Sürücü harfinin takip eden dışında)

   * Çift tırnak işareti (") (boşluk içeren yollar için tırnak işareti gerekmez.)

   * Küçüktür ( \< )

   * Büyüktür (>)

   * Soru işareti (?)

   * Yüzde işareti (%)

7. **Tamam** düğmesini seçin.

   ::: moniker range="vs-2017"

   > [!NOTE]
   > Eklenti projeleri oluşturulduğunda her zaman kaydedilir. Geçici projeler olarak oluşturulamaz. Geçici projeler hakkında daha fazla bilgi için bkz. [geçici projeler](../ide/creating-solutions-and-projects.md#create-a-temporary-project).

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>Belge düzeyi özelleştirme projesi oluşturmak için

1. **dosya** menüsünde **yeni**  >  **Project**' yi seçin. ıde 'niz Visual Basic geliştirme ayarlarını kullanacak şekilde ayarlandıysa, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

    **Yeni Proje** iletişim kutusu görünür.

2. şablonlar bölmesinde, kullanmak istediğiniz dilin düğümü altında **Office/SharePoint**' ı genişletin.

3. **Office eklentileri** düğümünü seçin.

4. Proje şablonları listesinde bir belge düzeyi proje şablonu seçin. kullanılabilir belge düzeyi proje şablonlarının listesi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > **Office eklentileri** düğümünü seçerken proje şablonları görünür değilse, **.NET Framework 4** veya sonraki bir sürümünün seçildiğinden emin olun.

5. **Ad** kutusuna proje için bir ad yazın. Bu ad, varsayılan olarak belge için de kullanılır. IDE 'niz Visual C# geliştirme ayarlarını veya genel geliştirme ayarlarını kullanacak şekilde ayarlandıysa, bir konum ve çözüm adı da girin.

   > [!NOTE]
   > Proje konumunun yolunda veya proje adında vekil karakterleri kullanamazsınız. Ayrıca, çözümü çevrimdışı kullanım için dağıtmayı planlıyorsanız, proje adındaki karakterlerin HTTP protokol belirtimlerine uyması gerekir.

6. **Tamam** düğmesini seçin.

    **Office için Visual Studio Araçları Project sihirbazı** açılır.

7. Çözüm için yeni bir belge oluşturmak istiyorsanız **Yeni belge oluştur** ' u seçin veya var olan bir belgeyi özelleştirmek istiyorsanız **mevcut bir belgeyi Kopyala** ' yı seçin.

    Yeni bir belge oluşturursanız **ad kutusunda adı** belirtin ve **Biçim** kutusunu kullanarak belgenin biçimini seçin. Kullanılabilir biçimler hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

    Mevcut bir belgeyi kullanıyorsanız, **mevcut belge kutusunun tam yolundaki** belgenin konumunu belirtin. Mutlak ve UNC yollarını kullanabilirsiniz. Belge için HTTP, FTP veya diğer protokol yollarını kullanmayın.

    Konumlar aşağıdaki biçimlere sahiptir:

   - [*sürücü*\]\:

   - \\\\*Sunucu* \\ *Paylaşma*

     Bu karakterleri konumda kullanmayın:

   - Yıldız işareti (*)

   - Dikey çubuk (|)

   - İki nokta (:) (Sürücü harfinin takip eden dışında)

   - Çift tırnak işareti (") (boşluk içeren yollar için tırnak işareti gerekmez.)

   - Küçüktür ( \< )

   - Büyüktür (>)

   - Soru işareti (?)

   - Yüzde işareti (%)

   > [!NOTE]
   > Bir projede var olan bir belgeyi kullanıyorsanız [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] , yalnızca ' de oluşturulan veya ' e dönüştürülen belgeleri kullanın [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . Benzer şekilde, bir Word 2010 projesinde varolan bir belgeyi kullanıyorsanız, yalnızca içinde oluşturulan veya Word 2010 ' e dönüştürülen belgeleri kullanın. Word 'ün önceki bir sürümünde oluşturulmuş bir belge kullanıyorsanız, belgede bazı özellikler devre dışı bırakılır. Bu özellikleri kullanan kodu yazmaya çalışırsanız, projenizde hatalarla karşılaşabilirsiniz. Bir belgeyi dönüştürmek için [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ya da Word 2010 ' de açın, Şeritteki **Dosya** sekmesinde **bilgi**  >  **Dönüştür**' ü seçin.

8. **Son**’u seçin.

9. Proje klasörünü ve alt klasörlerini aşağıdaki durumlarda Word içindeki güven merkezinde güvenilir konumlar listesine ekleyin:

   - *. docm* dosyasını temel alan bir Word belgesi oluşturuyorsunuz ve belge, bir VBA projesi veya Windows Forms denetimleri barındırır. Proje klasörünü güvenilen konumlar listesine eklemek, belgenin tasarım zamanında beklendiği gibi çalıştığından emin olmanıza yardımcı olur.

   - *. Dotx* dosyasını temel alan bir Word şablonu projesi oluşturuyorsunuz. Projeyi çalıştırıp hatalarını ayıklayabilmeniz için, proje klasörünü güvenilir konumlar listesine eklemeniz gerekir.

     güvenilen konumlara bir belge ekleme hakkında daha fazla bilgi için bkz. çevrimiçi web sitesi Microsoft Office [dosyalarınız için güvenilir bir konum oluşturma, kaldırma veya değiştirme](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="see-also"></a>Ayrıca bkz.
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [Office çözümlerin işbirliğine dayalı geliştirmesi](../vsto/collaborative-development-of-office-solutions.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [VSTO eklentileriyle çalışmaya başlama](../vsto/getting-started-programming-vsto-add-ins.md)
