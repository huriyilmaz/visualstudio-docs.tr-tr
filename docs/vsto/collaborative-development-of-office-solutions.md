---
title: Office çözümlerinin işbirlikçi geliştirmesi
description: Birden çok geliştiricinin bir Office projesi üzerinde diğer Visual Studio projelerinde birlikte çalıştıkları şekilde nasıl çalışabilecekleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 028530014afdc78ab6c9c0483c3d443195383793
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942314"
---
# <a name="collaborative-development-of-office-solutions"></a>Office çözümlerinin işbirlikçi geliştirmesi
  Birden çok geliştirici, diğer Visual Studio projelerinde birlikte çalıştıkları şekilde bir Office projesi üzerinde çalışabilir. Visual Studio, Office farklı konumlara yüklense bile, her bilgisayarda Microsoft Office yüklemesini doğru şekilde konumlandırır. Ancak farkında olmanız gereken bazı önemli noktalar vardır.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Hata ayıklama özellikleri paylaşılmıyor
 Hata ayıklama özellikleri, kaynak denetimi altındaki birden çok kullanıcı arasında paylaşılmaz. Visual Basic ve Visual C# projeleri, hata ayıklama özelliklerini kullanıcıya özgü bir dosyaya (*ProjectName*. vbproj. User veya *ProjectName*. csproj. User) depolar ve bu dosya kaynak denetimi altında değildir. Birden fazla kişinin hata ayıklaması varsa, her bir kişinin hata ayıklama özelliklerini el ile girmesi gerekir.

 Proje kaynak denetimi yerine bir ağ paylaşımında kullanılıyorsa, işbirliği geliştiricilerin çözümü açmasını ve derlemeyi test etmesini sağlamak için bazı ek adımlar gerçekleştirilmelidir.

## <a name="source-control-requires-checking-out-all-files"></a>Kaynak denetimi tüm dosyaları kullanıma alma gerektiriyor
 Projeleriniz için kaynak denetimi kullanıyorsanız, kod dosyasını her değiştirmenizde (örneğin, *ThisDocument*, *ThisWorkbook* veya *ThisAddIn* kodu dosyaları gibi) bir kod **Çözüm Gezgini** dosyası altındaki tüm dosyaları (örneğin, varsayılan olarak gizli olan dosyalar) denetlemeniz gerekir. Yalnızca en üst düzey kod dosyasına göz atın, değişiklikleriniz kaybolmuş olabilir.

 Değişikliklerinizi yaptıktan sonra, tüm dosyaları geri iade edin. Projelerde gizli kod dosyaları hakkında daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Bir ağ üzerinde resmi olmayan işbirliği için güvenlik
 Bir ağ konumunda (sunucuadı \ PaylaşımAdı) olan tüm belge düzeyi çözümler için \\ \\  \\ , üzerinde çalıştığınız Microsoft Office uygulamasındaki güvenilen klasör listesine tam nitelikli konum eklenmelidir. Ana klasörün altına alt dizinleri dahil etme seçeneğini belirleyin veya özel olarak hata ayıklama ve yapı klasörlerini güvenilen klasör listesine ekleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

 Derleme zamanında otomatik olarak oluşturulan geçici sertifikalar parolalarla güvenli değildir. Sertifikalar, geliştiricinin oturum açma adını ve diğer kişisel bilgilerini içerir. Geçici sertifikalar tarafından imzalanan özelleştirmeler dağıtırsanız, diğerleri bu bilgilere erişebiliyor olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
