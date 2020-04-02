---
title: Ofis çözümleri geliştirme genel bakış (VSTO)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abb58d30e33ab5cfe713175b40cd32f593921ae9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543944"
---
# <a name="office-solutions-development-overview-vsto"></a>Ofis çözümleri geliştirme genel bakış (VSTO)
  Microsoft Office'i çözümleriçin ön uç olarak kullanarak, Word'deki sözcük işleme özellikleri, Excel'in veri çözümleme özellikleri ve Outlook'un e-posta yönetimi özellikleri gibi tanıdık Microsoft Office kullanıcı arabirimlerinden ve araçlarından yararlanabilirsiniz. Office uygulamalarını özelleştirmek ve iş süreçleriniz için ihtiyacınız olan belirli özellikleri eklemek için Visual Studio'da çözümler geliştirebilirsiniz. Örneğin, Word'ü, önceden varolan veya güncellenebilir hale getirilebilen parçalardan sözleşmeleri birleştiren bir sözleşme üretecine dönüştürebilirsiniz. Excel ile, farklı projeler için özelleştirilmiş otomatik bir bütçe çalışma sayfası oluşturabilirsiniz. Kullanıcılarınız ofis çözümlerini çevrimdışı da alabilir ve bu da karmaşık çözümleri web tabanlı bir mimari kullandığınızda olduğundan daha pratik hale getirir.

 Bu konu, Visual Studio'daki Office geliştirici araçlarında bulunan Office için Visual Studio Araçları (VSTO) şablonlarını kullanarak oluşturabileceğiniz Office çözümleri türlerine genel bir bakış sağlar. Office ile nasıl geliştirilecekhakkında genel bilgi için [Office geliştirici merkezine](https://developer.microsoft.com/office)bakın.

## <a name="choose-an-office-project-type"></a>Office proje türü seçin
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSTO tabanlı Office geliştirme için aşağıdaki proje şablonları türlerini sağlar:

- **Belge düzeyinde özelleştirmeler** belirli bir belgeyle ilişkilidir.

- **VSTO Eklentileri** uygulamanın kendisi ile ilişkilidir.

  Bu proje türlerinden hangisinin çözümünüz için en iyi olduğuna karar vermek için, kodunuzun yalnızca belirli bir belge açıkken çalışmasını mı istediğinizi veya uygulama çalışırken kodun kullanılabilir olmasını isteyip istemediğiniz hakkında düşünün. Proje şablonları hakkında daha fazla bilgi için [Bkz. Office proje şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

  Oluşturabileceğiniz proje türleri, geliştirme bilgisayarına yüklediğiniz Office uygulamalarına bağlıdır. Daha fazla bilgi için Bkz. [Office uygulamasına ve proje türüne göre kullanılabilen Özellikler.](../vsto/features-available-by-office-application-and-project-type.md)

### <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler
 Belge düzeyindeözelleştirmeler, Microsoft Office Word veya Microsoft Office Excel'de tek bir belge, çalışma kitabı veya şablonla ilişkili bir derlemeden oluşur. İlişkili belge açıldığında montaj yüklenir. Oluşturduğunuz özelleştirmelerle ilgili özellikler yalnızca ilişkili belge açıkolduğunda kullanılabilir. Özelleştirmeler, herhangi bir belge açıkken yeni bir menü öğesi veya şerit sekmesi ni görüntülemek gibi uygulama genelinde değişiklik yapamaz.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]belge düzeyinde özelleştirmeler oluşturmanıza yardımcı olacak araçlar içerir. Özelleştirdiğiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]belge, denetimleri sürükleyip üzerine bırakarak belgeyi tasarlamanızı sağlayan bir tasarım yüzeyi olarak barındırılır. Windows [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Forms denetimleri, sürükle ve bırak veri bağlama ve tümleşik hata ayıklama gibi belge düzeyindeki projelerde birçok özellik mevcuttur.

 Özelleştirmeler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel için belge düzeyinde özelleştirmeleri programlamaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Word için belge düzeyinde özelleştirmeleri programlamaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO Eklentileri
 VSTO Eklentileri, Microsoft Office uygulamasıyla ilişkili bir derlemeden oluşur. Genellikle, ilişkili uygulama başlatıldığında VSTO Eklentisi çalışır, ancak kullanıcılar uygulama zaten çalışmaya başladıktan sonra VSTO Eklentileri de yükleyebilir. Oluşturduğunuz VSTO Eklentileri'ndeki özellikler, hangi belgelerin açık olduğuna bakılmaksızın uygulamanın kendisi tarafından kullanılabilir.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSTO Eklentileri oluşturmanıza yardımcı olacak araçlar içerir. Eklenti projeleri, VSTO Eklentisini temsil eden otomatik olarak oluşturulan bir sınıf içerir. Bu sınıf, VSTO Eklentisi yüklenip kapatıldığında ana bilgisayar uygulamasının nesne modeline erişmek ve kodu çalıştırmak için kullanabileceğiniz özellikler ve olaylar sağlar. Diğer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] birçok özellik, Windows Forms ve tümleşik hata ayıklama gibi VSTO Eklenti projelerinde kullanılabilir.

 VSTO Eklentileri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [VSTO Eklentileri programlamaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)

- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Birincil interop derlemelerini kullanarak Office uygulamalarını otomatikleştirin
 Uygulamanın nesne modeline erişen kod yazarak Office uygulamasının özelliklerini çözüme programlı olarak dahil edebilirsiniz. Nesne modelleri, çeşitli özellikler ve yöntemlerle işlevselliği ortaya çıkaran sınıfların bir düzenlemesidir. Her Office uygulaması için nesne modeli farklıdır.

 Office geliştirme araçlarını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]kullanarak oluşturulan bir çözümden Office uygulamasının nesne modelini kullanmak için, uygulama için birincil interop derlemesini (PIA) kullanmanız gerekir. PIA, çözümünüzün yönetilen kodunun Office uygulamasının COM tabanlı nesne modeliyle etkileşimkurmasını sağlar.

 Çoğu geliştirme görevini gerçekleştirmek için Office PI'lerini geliştirme bilgisayarınızdaki genel montaj önbelleğine yüklü ve kayıtlı olmalıdır. Daha fazla bilgi için [bkz.](../vsto/configuring-a-computer-to-develop-office-solutions.md) VSTO Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarda Office PI'leri gerekmez. Daha fazla bilgi için [Tasarım'a](../vsto/designing-and-creating-office-solutions.md)bakın ve Office çözümleri oluşturun.

 VSTO Office çözümlerinde PiA'ları kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)

- [Ofis birincil interop montajları](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Microsoft VSTO Office çözümlerini son kullanıcı bilgisayarlarda çalıştırma
 VsTO Office çözümü oluşturduğunuzda, dağıtım gereksinimlerinin geliştirme seçeneklerinizi nasıl etkileyebileceğini göz önünde bulundurun.

### <a name="deployment-options"></a>Dağıtım seçenekleri
 Office geliştirme araçlarını kullanarak oluşturduğunuz çözümleri dağıtmak için ClickOnce [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]veya Windows Installer'ı kullanın. ClickOnce dağıtımı, en az kullanıcı etkileşimi ile yüklenebilecek ve çalıştırılabilen kendi kendini güncelleştiren çözümler oluşturmanıza olanak tanır. Windows Installer (*.msi*) dosyaları son kullanıcı bilgisayarlarına kolayca dağıtılabilir veya Systems Management Server (SMS) kullanılarak dağıtılabilir. VSTO Office çözümlerini dağıtma hakkında daha fazla bilgi için [bkz.](../vsto/deploying-an-office-solution.md)

### <a name="install-prerequisites"></a>Ön koşulları yükleme
 Son kullanıcılar, Office geliştirme araçlarını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]kullanarak oluşturduğunuz bir çözümü çalıştırabilmeleri için önce, bilgisayarlarının belirli ön koşullar yüklü olması gerekir. ClickOnce'yi kullanarak veya bir Windows Installer dosyası oluşturarak çözümünüzü dağıtırsanız, bu ön koşullar çözümünüzle birlikte yüklenebilir. Daha fazla bilgi için dağıtım [için Office çözüm ön koşulları](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) ve nasıl olunması: Office [çözümlerini çalıştırmak için son kullanıcı bilgisayarlarına ön koşullar yükleyin.](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)

### <a name="security"></a>Güvenlik
 VSTO Office çözümleri için güvenlik, çözümü yüklerve yüklerken [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yaptığı bir dizi denetim tarafından uygulanır. Bu denetimler, dağıtım bildiriminin konumunun güvenilir olup olmadığını veya dağıtım bildirimini imzalamak için kullanılan sertifikanın güvenilir olup olmadığını doğrulamayı içerir. Daha fazla bilgi için [Secure Office çözümlerine](../vsto/securing-office-solutions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio&#41;'&#40;Office geliştirmeye başlayın](../vsto/getting-started-office-development-in-visual-studio.md)
- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Excel için belge düzeyinde özelleştirmeleri programlamaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Word için belge düzeyinde özelleştirmeleri programlamaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [VSTO Eklentileri programlamaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)
