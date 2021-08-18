---
title: Office çözümleri geliştirmeye genel bakış (VSTO)
description: word 'de sözcük işleme özellikleri ve Excel veri analizi özellikleri gibi tanıdık Microsoft Office kullanıcı arabirimleri ve araçları için özelleştirmeler geliştirmeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a105691896c5deec33a9d8ed6f28a6895b12546c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032426"
---
# <a name="office-solutions-development-overview-vsto"></a>Office çözümleri geliştirmeye genel bakış (VSTO)
  çözüm için ön uç olarak Microsoft Office kullanarak, word 'de sözcük işleme özellikleri, Excel veri analizi özellikleri ve Outlook e-posta yönetimi özellikleri gibi tanıdık Microsoft Office kullanıcı arabirimlerinden ve araçlarından yararlanabilirsiniz. Office uygulamaları özelleştirmek ve iş işlemleriniz için gereken belirli özellikleri eklemek üzere Visual Studio ' de çözümler geliştirebilirsiniz. Örneğin, Word 'Ü, düzenlenebilir veya düzenlenemez hale getirilen, önceden var olan parçaların dışına çeviren sözleşmeleri bir sözleşme oluşturucusuna dönüştürebilirsiniz. Excel, farklı projeler için özelleştirilmiş bir otomatik bütçe çalışma sayfası oluşturabilirsiniz. Kullanıcılarınız Ayrıca, Web tabanlı bir mimari kullanıyorsanız, karmaşık çözümlerin daha pratik olmasını sağlayan Office çözümlerini çevrimdışına alabilir.

 bu konu, Visual Studio Office geliştirici araçlarında bulunan Office için Visual Studio Araçları (VSTO) şablonları kullanarak oluşturabileceğiniz Office çözümlerin türlerine genel bakış sağlar. Office ile geliştirme hakkında genel bilgi için bkz. [Office geliştirici merkezi](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Office proje türü seçin
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSTO tabanlı Office geliştirme için aşağıdaki proje şablonu türlerini sağlar:

- **Belge düzeyi özelleştirmeleri** belirli bir belge ile ilişkilendirilir.

- **VSTO** eklentiler uygulamayla birlikte ilişkilendirilir.

  Çözümünüz için bu proje türlerinden hangisinin en iyisi olduğuna karar vermek için, kodunuzun yalnızca belirli bir belge açık olduğunda mı yoksa uygulamanın her çalıştığında kodun kullanılabilir olmasını mi istediğinizi düşünün. proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

  oluşturabileceğiniz proje türleri, geliştirme bilgisayarına yüklediğiniz Office uygulamalarına bağlıdır. daha fazla bilgi için bkz. [Office uygulama ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler
 belge düzeyi özelleştirmeleri, Microsoft Office Word veya Microsoft Office Excel tek bir belge, çalışma kitabı veya şablon ile ilişkili bir derlemeden oluşur. Derleme, ilişkili belge açıldığında yüklenir. Oluşturduğunuz özelleştirmelerdeki özellikler yalnızca ilişkili belge açık olduğunda kullanılabilir. Özelleştirmeler, herhangi bir belge açıkken yeni bir menü öğesi veya şerit sekmesi görüntüleme gibi uygulama genelinde değişiklikler yapamaz.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Belge düzeyinde özelleştirmeler oluşturmanıza yardımcı olacak araçlar içerir. Özelleştirdiğiniz belge içinde tasarım yüzeyi olarak barındırılır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve bu sayede denetimleri sürükleyip bırakarak belgeyi tasarlamanızı sağlar. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Windows Forms denetimleri, sürükle ve bırak veri bağlama ve tümleşik hata ayıklayıcı gibi belge düzeyi projelerde birçok diğer özellik mevcuttur.

 Özelleştirmeler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Word için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO Eklentiler
 VSTO eklentiler Microsoft Office uygulamayla ilişkili bir derlemeden oluşur. genellikle, VSTO eklentisi, ilişkili uygulama başlatıldığında çalışır, ancak kullanıcılar uygulama zaten çalıştıktan sonra VSTO eklentileri de yükleyebilir. oluşturduğunuz VSTO eklentilerdeki özellikler, hangi belgelerin açık olduğuna bakılmaksızın uygulamanın kendisi tarafından kullanılabilir.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSTO eklentiler oluşturmanıza yardımcı olacak araçlar içerir. eklenti projeleri, VSTO eklentisini temsil eden otomatik olarak oluşturulan bir sınıfı içerir. bu sınıf, ana bilgisayar uygulamasının nesne modeline erişmek ve VSTO eklentisi yüklendiğinde ve kapatıldığında kodu çalıştırmak için kullanabileceğiniz özellikler ve olaylar sağlar. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Windows Forms ve tümleşik hata ayıklayıcı gibi VSTO eklenti projelerinde birçok diğer özellik mevcuttur.

 VSTO eklentileri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [VSTO eklentileriyle çalışmaya başlama](../vsto/getting-started-programming-vsto-add-ins.md)

- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>birincil birlikte çalışma derlemelerini kullanarak Office uygulamaları otomatikleştirin
 uygulamanın nesne modeline erişen kod yazarak Office bir uygulamanın özelliklerini program aracılığıyla çözümünüze ekleyebilirsiniz. Nesne modelleri, işlevleri çeşitli özellikler ve yöntemlerle sunan sınıfların bir düzenlemesidir. her bir Office uygulaması için nesne modeli farklıdır.

 içinde Office geliştirme araçları kullanılarak oluşturulan bir çözümden Office uygulamasının nesne modelini kullanmak için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , uygulama için birincil birlikte çalışma derlemesini (pıa) kullanmanız gerekir. pıa, çözümünüzdeki yönetilen kodun Office uygulamasının COM tabanlı nesne modeliyle etkileşime geçmesini sağlar.

 çoğu geliştirme görevini gerçekleştirmek için Office pıa 'ları, geliştirme bilgisayarınızda genel derleme önbelleğinde yüklü ve kayıtlı olmalıdır. daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md). Office pıa 'ler, VSTO Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarında gerekli değildir. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

 VSTO Office çözümlerinde pıa 'leri kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)

- [birincil birlikte çalışma derlemelerini Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>son kullanıcı bilgisayarlarında Microsoft VSTO Office çözümlerini çalıştırma
 bir VSTO Office çözümü oluşturduğunuzda, dağıtım gereksinimlerinin geliştirme seçimlerinizi nasıl etkileyebileceğini göz önünde bulundurun.

### <a name="deployment-options"></a>Dağıtım seçenekleri
 içindeki Office geliştirme araçlarını kullanarak oluşturduğunuz çözümleri dağıtmak için ClickOnce veya Windows Installer kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . ClickOnce dağıtım, en az kullanıcı etkileşimi ile yüklenebilen ve çalıştırılabilen kendi kendini güncelleştiren çözümler oluşturmanıza olanak sağlar. Windows Yükleyici (*.msi*) dosyaları, son kullanıcı bilgisayarlarına kolayca dağıtılabilir veya Systems Management Server (SMS) kullanılarak dağıtılabilir. VSTO Office çözümlerini dağıtma hakkında daha fazla bilgi için bkz. [Office çözümü dağıtma](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Ön koşulları yükleme
 son kullanıcıların ' de Office geliştirme araçlarını kullanarak oluşturduğunuz bir çözümü çalıştırabilmeleri için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bilgisayarlarının bazı önkoşulların yüklü olması gerekir. çözümünüzü ClickOnce kullanarak veya bir Windows Installer dosyası oluşturarak dağıtırsanız, bu önkoşullar çözümünüzle birlikte yüklenebilir. daha fazla bilgi için bkz. [dağıtım için Office çözüm önkoşulları](/previous-versions/bb608617(v=vs.110)) ve [nasıl yapılır: Office çözümleri çalıştırmak için son kullanıcı bilgisayarlarına önkoşulları yüklemek](/previous-versions/bb608608(v=vs.110)).

### <a name="security"></a>Güvenlik
 VSTO Office çözümleri için güvenlik, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümü yüklediğinde ve yüklediğinde yaptığı bir dizi denetim tarafından zorlanır. Bu denetimler, dağıtım bildiriminin konumunun güvenilip güvenilmediğini veya dağıtım bildirimini imzalamak için kullanılan sertifikanın güvenilir olup olmadığını doğrulamaya dahildir. daha fazla bilgi için bkz. [Secure Office solutions](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Excel için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Word için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [VSTO eklentileriyle çalışmaya başlama](../vsto/getting-started-programming-vsto-add-ins.md)
