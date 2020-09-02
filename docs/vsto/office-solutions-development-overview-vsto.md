---
title: Office çözümleri geliştirmesine genel bakış (VSTO)
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80543944"
---
# <a name="office-solutions-development-overview-vsto"></a>Office çözümleri geliştirmesine genel bakış (VSTO)
  Çözüm için ön uç olarak Microsoft Office kullanarak, Word 'deki sözcük işleme özellikleri, Excel 'in veri analizi özellikleri ve Outlook 'un e-posta yönetimi özellikleri gibi tanıdık Microsoft Office Kullanıcı arabirimleri ve araçlarından faydalanabilirsiniz. Visual Studio 'da Office uygulamalarını özelleştirmek ve iş işlemleriniz için gereken belirli özellikleri eklemek için çözümler geliştirebilirsiniz. Örneğin, Word 'Ü, düzenlenebilir veya düzenlenemez hale getirilen, önceden var olan parçaların dışına çeviren sözleşmeleri bir sözleşme oluşturucusuna dönüştürebilirsiniz. Excel ile, farklı projeler için özelleştirilmiş bir otomatik bütçe çalışma sayfası oluşturabilirsiniz. Kullanıcılarınız Ayrıca, Web tabanlı bir mimari kullanıyorsanız, karmaşık çözümlerin daha pratik olmasını sağlayan Office çözümlerini çevrimdışına alabilir.

 Bu konu başlığı altında, Visual Studio 'da Office geliştirici araçları 'nda bulunan Office Visual Studio Araçları for Office (VSTO) şablonlarını kullanarak oluşturabileceğiniz Office çözümlerinin türlerine genel bakış sunulmaktadır. Office ile geliştirme hakkında genel bilgi için bkz. [Office Geliştirici Merkezi](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Office proje türü seçin
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , VSTO tabanlı Office geliştirme için aşağıdaki proje şablonu türlerini sağlar:

- **Belge düzeyi özelleştirmeleri** belirli bir belge ile ilişkilendirilir.

- **VSTO eklentileri** uygulamayla birlikte ilişkilendirilir.

  Çözümünüz için bu proje türlerinden hangisinin en iyisi olduğuna karar vermek için, kodunuzun yalnızca belirli bir belge açık olduğunda mı yoksa uygulamanın her çalıştığında kodun kullanılabilir olmasını mi istediğinizi düşünün. Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

  Oluşturabileceğiniz proje türleri, geliştirme bilgisayarına hangi Office uygulamalarına yüklediğinize bağlıdır. Daha fazla bilgi için bkz. [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler
 Belge düzeyi özelleştirmeleri, Microsoft Office Word veya Microsoft Office Excel 'de tek bir belge, çalışma kitabı veya şablon ile ilişkili bir derlemeden oluşur. Derleme, ilişkili belge açıldığında yüklenir. Oluşturduğunuz özelleştirmelerdeki özellikler yalnızca ilişkili belge açık olduğunda kullanılabilir. Özelleştirmeler, herhangi bir belge açıkken yeni bir menü öğesi veya şerit sekmesi görüntüleme gibi uygulama genelinde değişiklikler yapamaz.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Belge düzeyinde özelleştirmeler oluşturmanıza yardımcı olacak araçlar içerir. Özelleştirdiğiniz belge içinde tasarım yüzeyi olarak barındırılır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve bu sayede denetimleri sürükleyip bırakarak belgeyi tasarlamanızı sağlar. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Windows Forms denetimleri, sürükle ve bırak veri bağlama ve tümleşik hata ayıklayıcı gibi belge düzeyi projelerde birçok diğer özellik mevcuttur.

 Özelleştirmeler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel için belge düzeyi özelleştirmelerini Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Word için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO eklentileri
 VSTO eklentileri Microsoft Office uygulamayla ilişkili bir derlemeden oluşur. Genellikle, VSTO eklentisi, ilişkili uygulama başlatıldığında çalışır, ancak kullanıcılar, uygulama zaten çalıştıktan sonra VSTO Eklentilerini de yükleyebilir. Oluşturduğunuz belge, hangi belgeler açık olursa olsun, oluşturduğunuz VSTO Eklentilerindeki özellikler uygulamanın kendisi tarafından kullanılabilir.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , VSTO eklentileri oluşturmanıza yardımcı olan araçları içerir. Eklenti projeleri, VSTO eklentisini temsil eden otomatik olarak oluşturulan bir sınıfı içerir. Bu sınıf, konak uygulamasının nesne modeline erişmek ve VSTO eklentisi yüklendiğinde ve kapatıldığında kodu çalıştırmak için kullanabileceğiniz özellikler ve olaylar sağlar. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Windows Forms ve tümleşik bir hata ayıklayıcı gıbı VSTO eklentisi projelerinde birçok farklı özellik mevcuttur.

 VSTO eklentileri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)

- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerini kullanarak Office uygulamalarını otomatikleştirin
 Uygulamanın nesne modeline erişen kod yazarak bir Office uygulamasının özelliklerini program aracılığıyla çözümünüze ekleyebilirsiniz. Nesne modelleri, işlevleri çeşitli özellikler ve yöntemlerle sunan sınıfların bir düzenlemesidir. Her bir Office uygulaması için nesne modeli farklıdır.

 İçindeki Office geliştirme araçları kullanılarak oluşturulan bir çözümden Office uygulamasının nesne modelini kullanmak için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , uygulama için birincil birlikte çalışma derlemesini (PIA) kullanmanız gerekir. PIA, çözümünüzdeki yönetilen kodun Office uygulamasının COM tabanlı nesne modeliyle etkileşime geçmesini sağlar.

 Geliştirme görevlerinin çoğunu gerçekleştirmek için Office PIA 'Ları geliştirme bilgisayarınızda genel derleme önbelleğinde yüklü ve kayıtlı olmalıdır. Daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md). Office PIA 'leri, VSTO Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarında gerekli değildir. Daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

 VSTO Office çözümlerinde PIA 'leri kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)

- [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında Microsoft VSTO Office çözümlerini çalıştırma
 Bir VSTO Office çözümü oluşturduğunuzda, dağıtım gereksinimlerinin geliştirme seçimlerinizi nasıl etkileyebileceğini göz önünde bulundurun.

### <a name="deployment-options"></a>Dağıtım seçenekleri
 İçindeki Office geliştirme araçlarını kullanarak oluşturduğunuz çözümleri dağıtmak için ClickOnce veya Windows Installer kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . ClickOnce dağıtımı, en az kullanıcı etkileşimi ile yüklenebilen ve çalıştırılabilen kendi kendini güncelleştiren çözümler oluşturmanıza olanak sağlar. Windows Installer (*. msi*) dosyaları, son kullanıcı bilgisayarlarına kolayca dağıtılabilir veya Systems Management Server (SMS) kullanılarak dağıtılabilir. VSTO Office çözümlerini dağıtma hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Ön koşulları yükleme
 Son kullanıcıların ' de Office geliştirme araçları 'nı kullanarak oluşturduğunuz bir çözümü çalıştırabilmeleri için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bilgisayarlarının belirli önkoşulların yüklü olması gerekir. Çözümünüzü ClickOnce kullanarak veya bir Windows Installer dosyası oluşturarak dağıtırsanız, bu önkoşullar çözümünüzle birlikte yüklenebilir. Daha fazla bilgi için bkz. [dağıtım Için Office çözüm önkoşulları](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) ve [nasıl yapılır: Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarına önkoşulları yüklemek](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

### <a name="security"></a>Güvenlik
 VSTO Office çözümleri için güvenlik, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümü yüklediğinde ve yüklediğinde yaptığı bir dizi denetim tarafından zorlanır. Bu denetimler, dağıtım bildiriminin konumunun güvenilip güvenilmediğini veya dağıtım bildirimini imzalamak için kullanılan sertifikanın güvenilir olup olmadığını doğrulamaya dahildir. Daha fazla bilgi için bkz. [güvenli Office çözümleri](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Excel için belge düzeyi özelleştirmelerini Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Word için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)
