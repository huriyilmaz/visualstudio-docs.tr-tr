---
title: Office çözümlerine genel bakış (VSTO)
description: Word'de sözcük işleme özellikleri ve Microsoft Office analizi özellikleri gibi bilinen kullanıcı arabirimleri ve araçları için özelleştirmeler geliştirmeyi Excel.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633838"
---
# <a name="office-solutions-development-overview-vsto"></a>Office çözümlerine genel bakış (VSTO)
  Çözümler için Microsoft Office'ı ön uç olarak kullanarak Word'de sözcük işleme özellikleri, Excel'nin veri analizi özellikleri ve Outlook'nin e-posta yönetimi özellikleri gibi bilindik Microsoft Office kullanıcı arabirimlerinden ve araçlardan Outlook. Uygulamalarınızı özelleştirmek ve iş Visual Studio ihtiyaç Office özellikleri eklemek için bu hizmetlerde çözümler geliştirebilirsiniz. Örneğin Word'i, önceden mevcut olan ve düzenlenebilir veya düzenlenemez hale gelebilir parçalardan anlaşmaları bir araya toplayacak bir anlaşma oluşturucuya dönüştürün. Bu Excel, farklı projeler için özelleştirilmiş bir otomatik bütçe çalışma sayfası oluşturabilirsiniz. Kullanıcılarınız ofis çözümlerini çevrimdışına alarak karmaşık çözümleri web tabanlı mimariden daha pratik hale de getirmenizi sağlar.

 Bu konu, Office geliştirici araçlarında bulunan Office için Visual Studio Araçları (VSTO) şablonlarını kullanarak oluşturabilirsiniz Office çözüm türlerine genel bir bakış Visual Studio. Ile geliştirme hakkında genel bilgi için Office geliştirici merkezine [Office bakın.](https://developer.microsoft.com/office)

## <a name="choose-an-office-project-type"></a>Bir proje Office seçin
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]uygulama tabanlı geliştirme için aşağıdaki proje VSTO türlerini Office sağlar:

- **Belge düzeyinde özelleştirmeler** belirli bir belgeyle ilişkilendirilmektedir.

- **VSTO eklentileri uygulamanın** kendisiyle ilişkilendirildi.

  Bu proje türlerinden hangisinin çözümünüz için en uygun olduğuna karar vermek için, kodunuzun yalnızca belirli bir belge açık olduğunda mı yoksa uygulama her çalıştırıda kodun kullanılabilir olup olmadığını düşünme. Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

  Oluştur oluşturabilirsiniz proje türleri, geliştirme Office hangi uygulamaları yüklemiş olduğunu bağlıdır. Daha fazla bilgi için [bkz. Uygulama ve Office tarafından kullanılabilen özellikler.](../vsto/features-available-by-office-application-and-project-type.md)

### <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler
 Belge düzeyinde özelleştirmeler, Word veya Microsoft Office'de tek bir belge, çalışma kitabı veya şablonla ilişkilendirilmiş bir derlemeden Microsoft Office Excel. İlişkili belge açıldığında derleme yüklenir. Oluştursanız özelleştirmelerde özellikler yalnızca ilişkili belge açık olduğunda kullanılabilir. Özelleştirmeler, herhangi bir belge açıkken yeni bir menü öğesini veya şerit sekmesini görüntüleme gibi uygulama genelinde değişiklik yapmaz.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , belge düzeyinde özelleştirmeler oluşturmanıza yardımcı olacak araçlar içerir. Özelleştirebileceğiniz belge, üzerinde denetim sürükleyip bırakarak belgeyi tasarlamanıza olanak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlayan bir tasarım yüzeyi olarak barındırıldı. Windows Forms denetimleri, sürükle bırak veri bağlama ve tümleşik hata ayıklayıcısı gibi belge düzeyindeki projelerde başka [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] birçok özellik de mevcuttur.

 Özelleştirmeler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Kullanmaya başlayın için belge düzeyinde özelleştirmeler programlama Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Kullanmaya başlayın word için belge düzeyinde özelleştirmeler programlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO Eklentiler
 VSTO Eklentiler, bir uygulamayla ilişkili bir derlemeden Microsoft Office oluşur. Genellikle, VSTO uygulama çalışmaya başladıktan sonra kullanıcılar eklentilerini de VSTO eklentilerini de yükleyene kadar uygulama eklentilerini çalıştırır. Oluştur VSTO eklentilerin özellikleri, hangi belgelerin açık olduğuna bakılmaksızın uygulamanın kendisinde kullanılabilir.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], eklentilerini oluşturmanıza yardımcı VSTO araçlar içerir. Eklenti projeleri, eklentiyi temsil eden otomatik olarak oluşturulmuş bir VSTO içerir. Bu sınıf, konak uygulamanın nesne modeline erişmek için kullanabileceğiniz özellikler ve olaylar sağlar ve VSTO eklenti yükleniyor ve kapatıyor. Windows Forms ve tümleşik hata ayıklayıcı gibi diğer birçok özellik [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSTO Eklenti projelerinde kullanılabilir.

 Eklenti ekleme hakkında VSTO için aşağıdaki konulara bakın:

- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)

- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Birincil Office derlemelerini kullanarak uygulamaları otomatikleştirme
 Uygulamanın nesne modeline erişen kod yazarak Office uygulamanın özelliklerini program aracılığıyla çözümünüzle bir arada bulundurabilirsiniz. Nesne modelleri, çeşitli özellikler ve yöntemler aracılığıyla işlevselliği ortaya çıkaran sınıfların düzenidir. Her bir uygulama için Office modeli farklıdır.

 içinde Office geliştirme araçları kullanılarak oluşturulan bir çözümden bir Office uygulamanın nesne modelini kullanmak için, uygulama için birincil birlikte çalışma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] derlemesi (PIA) kullan gerekir. PIA, çözümünüzde yönetilen kodun uygulamanın COM Office modeliyle etkileşim kurmalarına olanak sağlar.

 Geliştirme görevlerinin çoğunu Office için geliştirme bilgisayarınızda genel derleme önbelleğinde yüklü ve kayıtlı olan genel PIA'ların olması gerekir. Daha fazla bilgi için, [bkz. Configure a computer to develop Office .](../vsto/configuring-a-computer-to-develop-office-solutions.md) Bu Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarında farklı PIA'VSTO Office gerekmez. Daha fazla bilgi için [bkz. Özel çözümler Office oluşturma.](../vsto/designing-and-creating-office-solutions.md)

 Farklı çözümlerde PIA'ları kullanma hakkında VSTO Office için aşağıdaki konulara bakın:

- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)

- [Office birlikte çalışma derlemelerini birleştirme](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Son kullanıcı VSTO Office Microsoft VSTO Office çözümlerini çalıştırma
 Yeni bir çözüm VSTO Office dağıtım gereksinimlerinin geliştirme seçimlerinizi nasıl etkileyeceğini göz önünde bulundurabilirsiniz.

### <a name="deployment-options"></a>Dağıtım seçenekleri
 'ClickOnce geliştirme Windows kullanarak oluştursanız çözümleri dağıtmak için Office yükleyicisini [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanın. ClickOnce dağıtımı, çok az kullanıcı etkileşimiyle yüklenilen ve çalıştırılana kendi kendini güncelleştiren çözümler oluşturmanıza olanak sağlar. Windows Yükleyici (*.msi*) dosyaları son kullanıcı bilgisayarlara kolayca dağıtılabiliyor veya Systems Management Server (SMS) kullanılarak dağıtılabiliyor. Çözüm dağıtma hakkında daha fazla VSTO Office için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

### <a name="install-prerequisites"></a>Ön koşulları yükleme
 Son kullanıcıların içinde uygulama geliştirme araçlarını kullanarak oluşturacakları bir Office önce, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bilgisayarlarında belirli önkoşullar yüklü olması gerekir. Çözümlerinizi ClickOnce kullanarak veya Windows Yükleyici dosyası oluşturarak dağıtırsanız, bu önkoşullar çözümünüzle birlikte yükleyebilirsiniz. Daha fazla bilgi için [bkz. Office](/previous-versions/bb608617(v=vs.110)) için çözüm önkoşulları ve Nasıl kullanılır: Son kullanıcı bilgisayarlarına önkoşulları yükleme ve [Office çalıştırma.](/previous-versions/bb608608(v=vs.110))

### <a name="security"></a>Güvenlik
 Çözüm VSTO Office için güvenlik, çözümü yüklerken ve yüklerken tarafından yapılan bir dizi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] denetimle zorlar. Bu denetimler dağıtım bildiriminin konumunun güvenilir olup olmadığını veya dağıtım bildirimini imzalamak için kullanılan sertifikanın güvenilir olup olmadığını doğrulamayı içerir. Daha fazla bilgi için [bkz. Güvenli Office çözümleri.](../vsto/securing-office-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Kullanmaya başlayın için belge düzeyinde özelleştirmeler programlama Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Kullanmaya başlayın word için belge düzeyinde özelleştirmeler programlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)
