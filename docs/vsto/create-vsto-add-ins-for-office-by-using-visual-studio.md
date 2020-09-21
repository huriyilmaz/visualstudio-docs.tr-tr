---
title: Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e8cd25b8c4c70067641468dd6fa321e9e4fbe39
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809368"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
  Office 'i genişleten .NET Framework uygulamalar oluşturmak için Visual Studio 'daki Microsoft Office Geliştirici Araçları ' nı kullanabilirsiniz. Bu uygulamalar *Office çözümleri*olarak da adlandırılır.

 Office geliştirici araçları, çeşitli iş ihtiyaçlarını karşılamak için Office çözümleri oluşturmanıza yardımcı olan özellikler sağlar. Araçlar, Visual Basic veya Visual C# ' yi kullanarak Office çözümleri oluşturmanıza yardımcı olan proje şablonlarını ve Office çözümleriniz için özel kullanıcı arabirimleri oluşturmanıza yardımcı olan görsel tasarımcıları içerir.

[!include[Add-ins note](includes/addinsnote.md)]

 Office geliştirme hakkında en son bilgiler için [Microsoft Office Geliştirici Merkezi](https://developer.microsoft.com/office/docs)' ne bakın.

## <a name="in-this-section"></a>Bu bölümde
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](getting-started-office-development-in-visual-studio.md)

 Office çözümleri oluşturmak için bir geliştirme bilgisayarı yapılandırma, Office çözümlerini oluşturmaya başlama ve Visual Studio 'da Office geliştirmeye yönelik yenilikler hakkında bilgilere bağlantılar sağlar.

- [Office çözümlerini yükseltme ve geçirme](upgrading-and-migrating-office-solutions.md)

 Visual Studio 'nun önceki sürümleri kullanılarak oluşturulan projelere yönelik yükseltme işlemi hakkındaki bilgilere bağlantılar sağlar.

- [Visual Studio 'da Office çözümlerinin mimarisi](architecture-of-office-solutions-in-visual-studio.md)

 Belge düzeyi özelleştirmeleri ve VSTO eklentileri hakkında bilgiler de dahil olmak üzere Office çözümlerinin nasıl çalıştığı hakkında bilgi için bağlantılar sağlar.

- [Office çözümleri tasarlama ve oluşturma](designing-and-creating-office-solutions.md)

 Visual Studio 'da bir Office projesi oluşturma ve projenizi yapılandırma hakkında bilgi sağlar.

- [Office çözümleri geliştirme](developing-office-solutions.md)

 Office Kullanıcı arabirimini özelleştirme, verilerle çalışma ve sorunları giderme dahil olmak üzere Office çözümleriyle yönetilen kod kullanma hakkında bilgi sağlar.

- [Excel çözümleri](excel-solutions.md)

 Excel 'in otomatikleştirilmesi, Excel çözümleri oluşturulması ve Excel 'e özgü Genelleştirme sorunlarını anlama hakkında bilgi sağlar.

- [InfoPath çözümleri](infopath-solutions.md)

 InfoPath için form şablonları ve VSTO eklentileri oluşturma hakkında bilgi sağlar.

- [Outlook çözümleri](outlook-solutions.md)

 Outlook 'U otomatikleştirme ve Outlook VSTO eklentileri ve form bölgeleri oluşturma hakkında bilgi sağlar.

- [PowerPoint çözümleri](powerpoint-solutions.md)

 PowerPoint 'i otomatikleştirme ve PowerPoint VSTO eklentileri oluşturma hakkında bilgi sağlar.

- [Proje çözümleri](project-solutions.md)

 Microsoft Office projenin otomatikleştirilmesi ve proje VSTO eklentileri oluşturulması hakkında bilgi sağlar.

- [Visio çözümleri](visio-solutions.md)

 Visio 'Yu otomatikleştirme ve Visio VSTO eklentileri oluşturma hakkında bilgi sağlar.

- [Word çözümleri](word-solutions.md)

 Word 'Ü otomatikleştirme ve Word çözümlerini oluşturma hakkında bilgi sağlar.

- [Office çözümleri oluşturma](building-office-solutions.md)

 İçindeki Office projelerini ve diğer proje türlerini oluşturma arasındaki farklılıklar hakkında bilgi sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Office projelerinde hata ayıklama](debugging-office-projects.md)

 İçindeki Office projelerinin hata ayıklaması ve diğer proje türleri arasındaki farklar hakkında bilgi sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Güvenli Office çözümleri](securing-office-solutions.md)

 Office çözümlerinde güvenlik özelliklerinin nasıl çalıştığı hakkında bilgi sağlar.

- [Office çözümünü dağıtma](deploying-an-office-solution.md)

 Office çözümlerini kullanıcılarınız için nasıl kullanılabilir hale getirmek ve bir dağıtım yöntemi seçerken göz önünde bulundurmanız gereken önemli sorunlar hakkında bilgi sağlar.

- [Office geliştirme örnekleri ve izlenecek yollar](office-development-samples-and-walkthroughs.md)

 Ortak görevleri gerçekleştirmeye yönelik adım adım yönergeler veren örnek uygulamalara ve konulara bağlantılar sağlar.

- [Visual Studio 'da Office geliştirme &#40;Genel başvuru&#41;](general-reference-office-development-in-visual-studio.md)

 Office birincil birlikte çalışma derlemeleri, bildirimleri, Kullanıcı arabirimi öğeleri ve hata iletileri hakkında ayrıntılı bilgi için bağlantılar sağlar.

- [Visual Studio 'da Office geliştirme &#40;yönetilen başvuru&#41;](managed-reference-office-development-in-visual-studio.md)

 ' İ hedefleyen Office projelerinde kullanılan API ad alanları ve türleri hakkında bilgi bağlantıları sağlar [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . .NET Framework 3,5 ' i hedefleyen Office projelerinde kullanılan ad alanları ve türler hakkında API başvuru belgeleri için, Visual Studio 2008 belgelerindeki aşağıdaki başvuru bölümüne bakın: [2007 sistem tarafından yönetilen başvuru](managed-reference-office-development-in-visual-studio.md).

- [Yönetilmeyen API başvurusu &#40;Visual Studio 'da Office geliştirme&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Office uygulamalarında yönetilen VSTO Eklentilerini yükleme ve kaldırma gibi eylemleri gerçekleştirmek için kullanabileceğiniz COM arabirimleri hakkında bilgi bağlantıları içerir.

## <a name="related-sections"></a>İlgili bölümler
- [Visual Studio Geliştirici Portalı Ile Office geliştirme](https://developer.microsoft.com/office/docs) Teknik makaleler, videolar ve blogları gibi ek kaynaklar sağlar.

- [Visual Studio Geliştirici Merkezi](https://visualstudio.microsoft.com/) Teknik makaleler, videolar ve blogları gibi ek Visual Studio kaynakları sağlar.

- [MSDN Kitaplığı 'nın Microsoft Office geliştirme bölümü](/previous-versions/office/office-12/bb726434(v=office.12)) MSDN Kitaplığı 'nın çeşitli Office sürümleri (Visual Studio kullanarak Office geliştirmeye özgü değil) için çözümler geliştirme hakkında makaleler ve başvuru belgeleri bulabileceğiniz alanı.

- [Visual Studio 'Da uygulama geliştirme](/previous-versions/h8w79z10(v=vs.140)) Web uygulamaları, XML Web Hizmetleri ve geleneksel istemci uygulamaları tasarlamak, geliştirmek, hatalarını ayıklamak ve dağıtmak için Visual Studio 'Yu nasıl kullanabileceğinizi açıklayan konuların bağlantılarını içerir.

- [Visual Studio 'da .NET Framework programlama](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Visual Basic ve Visual C# ' de .NET Framework ile uygulama geliştirmeyi anlatır.