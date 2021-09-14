---
title: Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
description: Office genişleten .NET Framework uygulamalar oluşturmak için Visual Studio Microsoft Office geliştirici araçlarını nasıl kullanabileceğinizi öğrenin.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 46330c69b89b297b82ce70d3fb6eb0b7bd7d95df
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725608"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
> [!IMPORTANT]
> VSTO [.NET Framework](/dotnet/framework/get-started/overview)bağlıdır. COM eklentileri de .NET Framework yazılabilir. Office Eklentiler .net [Core ve .NET 5 +](/dotnet/core/dotnet-five)ile birlikte oluşturulamaz ve en son .net sürümleridir. bunun nedeni, .net Core/. NET 5 + ' ın aynı işlemde .NET Framework birlikte çalışamadığı ve eklenti yükleme hatalarına neden olabilir. Office için VSTO ve COM eklentilerini yazmak üzere .NET Framework kullanmaya devam edebilirsiniz. Microsoft, .net Core veya .net 5 + kullanacak şekilde VSTO veya COM eklentisi platformunu güncelleştirmemelidir. [Office Web](/office/dev/add-ins/overview/office-add-ins)eklentilerinin sunucu tarafını oluşturmak için ASP.NET Core dahil .net Core ve .net 5 + avantajlarından faydalanabilirsiniz.

  Office genişleten .NET Framework uygulamalar oluşturmak için Visual Studio Microsoft Office geliştirici araçlarını kullanabilirsiniz. bu uygulamalar *Office çözümleri* olarak da adlandırılır.

 Office geliştirici araçları, çeşitli iş ihtiyaçlarını karşılamak için Office çözümleri oluşturmanıza yardımcı olan özellikler sağlar. araçlar, Visual Basic veya visual C# kullanarak Office çözümleri oluşturmanıza yardımcı olan proje şablonlarını ve Office çözümleriniz için özel kullanıcı arabirimleri oluşturmanıza yardımcı olan görsel tasarımcıları içerir.

[!include[Add-ins note](includes/addinsnote.md)]

 Office geliştirme hakkında en son bilgiler için bkz. [Microsoft Office geliştirici merkezi](https://developer.microsoft.com/office/docs).

## <a name="in-this-section"></a>Bu bölümde
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](getting-started-office-development-in-visual-studio.md)

 Office çözümleri oluşturmak için bir geliştirme bilgisayarı yapılandırma, Office çözümleri oluşturmaya başlama ve Visual Studio Office geliştirmeye yönelik yenilikler hakkında bilgiler sağlar.

- [Office çözümlerini yükseltme ve geçirme](upgrading-and-migrating-office-solutions.md)

 Visual Studio önceki sürümleri kullanılarak oluşturulan projelere yönelik yükseltme işlemi hakkındaki bilgilere bağlantılar sağlar.

- [Visual Studio Office çözümlerin mimarisi](architecture-of-office-solutions-in-visual-studio.md)

 belge düzeyi özelleştirmeleri ve VSTO eklentileri hakkında bilgiler de dahil olmak üzere Office çözümlerin nasıl çalıştığı hakkında bilgi için bağlantılar sağlar.

- [Office çözümleri tasarlama ve oluşturma](designing-and-creating-office-solutions.md)

 Office projesi oluşturma ve projenizi Visual Studio yapılandırma hakkında bilgi sağlar.

- [Office çözümleri geliştirme](developing-office-solutions.md)

 Office kullanıcı arabirimini özelleştirme, verilerle çalışma ve sorunları giderme dahil olmak üzere Office çözümleri ile yönetilen kod kullanma hakkında bilgi sağlar.

- [Excel çözümleri](excel-solutions.md)

 Excel otomatikleştirme, Excel çözümleri oluşturma ve Excel özgü genelleştirme sorunlarını anlama hakkında bilgiler sağlar.

- [InfoPath çözümleri](infopath-solutions.md)

 form şablonlarının nasıl oluşturulacağı ve ınfopath için VSTO eklentilerin nasıl oluşturulacağı hakkında bilgi sağlar.

- [Outlook çözümleri](outlook-solutions.md)

 Outlook otomatikleştirip Outlook VSTO eklentileri ve form bölgelerini oluşturma hakkında bilgi sağlar.

- [PowerPoint çözümleri](powerpoint-solutions.md)

 PowerPoint otomatikleştirme ve PowerPoint VSTO eklentileri oluşturma hakkında bilgi sağlar.

- [Project çözümleri](project-solutions.md)

 Microsoft Office projenin otomatikleştirilmesi ve proje VSTO eklentileri oluşturulması hakkında bilgi sağlar.

- [Visio çözümleri](visio-solutions.md)

 Visio otomatikleştirme ve Visio VSTO eklentileri oluşturma hakkında bilgi sağlar.

- [Word çözümleri](word-solutions.md)

 Word 'Ü otomatikleştirme ve Word çözümlerini oluşturma hakkında bilgi sağlar.

- [Office çözümleri oluşturun](building-office-solutions.md)

 ' deki Office projeleri ve diğer proje türleri arasındaki farklılıklar hakkında bilgi sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Office projelerinde hata ayıklama](debugging-office-projects.md)

 içindeki hata ayıklama Office projeleri ve diğer proje türleri arasındaki farklılıklar hakkında bilgi sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Office çözümleri güvenli hale getirme](securing-office-solutions.md)

 güvenlik özelliklerinin Office çözümlerinde nasıl çalıştığı hakkında bilgi sağlar.

- [Office çözümünü dağıtma](deploying-an-office-solution.md)

 kullanıcılarınız için Office çözümlerin nasıl kullanılabileceğini ve bir dağıtım yöntemi seçerken göz önünde bulundurmanız gereken başlıca sorunları hakkında bilgi sağlar.

- [Office geliştirme örnekleri ve izlenecek yollar](office-development-samples-and-walkthroughs.md)

 Ortak görevleri gerçekleştirmeye yönelik adım adım yönergeler veren örnek uygulamalara ve konulara bağlantılar sağlar.

- [genel başvuru &#40;Office geliştirme Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Office birincil birlikte çalışma derlemeleri, bildirimleri, kullanıcı arabirimi öğeleri ve hata iletileri hakkında ayrıntılı bilgi için bağlantılar sağlar.

- [yönetilen başvuru &#40;Office geliştirme Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 ' i hedefleyen Office projelerinde kullanılan apı ad alanları ve türleri hakkında bilgi bağlantıları sağlar [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . .NET Framework 3,5 ' i hedefleyen Office projelerinde kullanılan ad alanları ve türler hakkında apı başvuru belgeleri için Visual Studio 2008 belgelerindeki şu başvuru bölümüne bakın: [2007 sistem tarafından yönetilen başvuru](managed-reference-office-development-in-visual-studio.md).

- [yönetilmeyen apı başvurusu &#40;Office geliştirme Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Office uygulamalarında yönetilen VSTO eklentilerini yükleme ve kaldırma gibi eylemleri gerçekleştirmek için kullanabileceğiniz COM arabirimleri hakkında bilgi bağlantıları içerir.

## <a name="related-sections"></a>İlgili bölümler
- [Visual Studio geliştirici portalı ile Office geliştirme](https://developer.microsoft.com/office/docs) Teknik makaleler, videolar ve blogları gibi ek kaynaklar sağlar.

- [Visual Studio geliştirici merkezi](https://visualstudio.microsoft.com/) teknik makaleler, videolar ve blogları gibi ek Visual Studio kaynaklar sağlar.

- [MSDN kitaplığı 'nın Microsoft Office geliştirme bölümü](/previous-versions/office/office-12/bb726434(v=office.12)) MSDN kitaplığı 'nın, Office birkaç sürümü (Visual Studio kullanarak Office geliştirmeye özgü değil) için çözümler geliştirme hakkında makaleler ve başvuru belgeleri bulabileceğiniz bir alandır.

- [Visual Studio 'de uygulama geliştirme](/previous-versions/h8w79z10(v=vs.140)) web uygulamaları, XML web hizmetleri ve geleneksel istemci uygulamaları tasarlamak, geliştirmek, hatalarını ayıklamak ve dağıtmak için Visual Studio nasıl kullanabileceğinizi açıklayan konuların bağlantılarını içerir.

- [Visual Studio .NET Framework programlama](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Visual Basic ve Visual C# ' de .NET Framework ile uygulama geliştirmeyi anlatır.
