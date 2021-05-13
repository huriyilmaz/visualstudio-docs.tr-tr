---
title: Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
description: Office'i genişleten yeni Microsoft Office oluşturmak için Visual Studio geliştirici araçlarını .NET Framework nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
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
ms.workload:
- office
ms.openlocfilehash: 990caeec642a745bec5b6e0f2d29ff5d6213d095
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848324"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
> [!IMPORTANT]
> VSTO, [.NET Framework.](https://docs.microsoft.com/dotnet/framework/get-started/overview) COM eklentileri de .NET Framework. Office Eklentileri,.NET Core ve [.NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five)ile oluşturulamaz. Bu, .NET'in en son sürümleridir. Bunun nedeni.NET Core/.NET 5+ ile aynı işlemde .NET Framework birlikte çalışamaz ve eklenti yük hatalarına yol açabilir. Office için VSTO .NET Framework COM eklentilerini yazmak üzere .NET Framework kullanmaya devam edebilirsiniz. Microsoft, VSTO veya COM eklenti platformunu .NET Core veya .NET 5+ kullanmak üzere güncelleştirmez. Office Web Eklentileri'nin sunucu tarafını oluşturmak için .NET Core ve .NET 5+ ASP.NET Core'dan [faydalanabilirsiniz.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  Office'i genişleten Microsoft Office uygulamaları Visual Studio için .NET Framework geliştirici araçlarını kullanabilirsiniz. Bu uygulamalar, Office çözümleri *olarak da adlandırılmıştır.*

 Office geliştirici araçları, çeşitli iş ihtiyaçlarına uygun Office çözümleri oluşturmanıza yardımcı olan özellikler sağlar. Araçlar, Visual Basic veya Visual C# kullanarak Office çözümleri oluşturmanıza yardımcı olacak proje şablonlarını ve Office çözümleriniz için özel kullanıcı arabirimleri oluşturmanıza yardımcı olan görsel tasarımcıları içerir.

[!include[Add-ins note](includes/addinsnote.md)]

 Office geliştirme hakkında en son bilgiler için bkz. [Microsoft Office merkezi.](https://developer.microsoft.com/office/docs)

## <a name="in-this-section"></a>Bu bölümde
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Bir geliştirme bilgisayarlarını Office çözümleri oluşturmak üzere yapılandırma, Office çözümleri oluşturmaya başlama ve Office'te Office geliştirmeye yönelik yeni Visual Studio.

- [Office çözümlerini yükseltme ve geçirme](upgrading-and-migrating-office-solutions.md)

 Önceki sürümler kullanılarak oluşturulan projelerin yükseltme işlemiyle ilgili bilgilerin bağlantılarını Visual Studio.

- [Office çözümlerinin Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Belge düzeyi özelleştirmeler ve VSTO Eklentileri hakkında bilgiler de dahil olmak üzere Office çözümlerinin nasıl çalışmalarına ilişkin bilgilerin bağlantılarını sağlar.

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

 Office projelerinde hata ayıklama ile 'de diğer proje türleri arasındaki farklar hakkında bilgi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlar.

- [Güvenli Office çözümleri](securing-office-solutions.md)

 Office çözümlerde güvenlik özelliklerinin çalışması hakkında bilgi sağlar.

- [Office çözümü dağıtma](deploying-an-office-solution.md)

 Office çözümlerini kullanıcılarınız için kullanılabilir hale nasıl ek olarak dağıtım yöntemi seçtiğinize ilişkin önemli sorunlar hakkında bilgi sağlar.

- [Office geliştirme örnekleri ve izlenecek yollar](office-development-samples-and-walkthroughs.md)

 Genel görevleri gerçekleştirmeye ilişkin adım adım yönergeler sağlayan örnek uygulamalara ve konulara bağlantılar sağlar.

- [Office geliştirme &#40;genel başvuru Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Office birincil birlikte çalışma derlemeleri, bildirimleri, kullanıcı arabirimi öğeleri ve hata iletileri hakkında ayrıntılı bilgilerin bağlantılarını sağlar.

- [Office &#40;yönetilen başvuru Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 API ad alanları ve hedef Office projelerinde kullanılan türleri hakkında bilgi bağlantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sağlar. .NET Framework 3.5'i hedef alan Office projelerinde kullanılan ad alanları ve türleri hakkında API başvurusu belgeleri için, Visual Studio 2008 belgelerinde aşağıdaki başvuru bölümüne [bakın: 2007](managed-reference-office-development-in-visual-studio.md)sistem tarafından yönetilen başvuru.

- [Office geliştirmesinde &#40;API başvurusu Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Office uygulamalarında yönetilen VSTO Eklentilerini yükleme ve kaldırma gibi eylemleri gerçekleştirmek için kullanabileceğiniz COM arabirimleri hakkında bilgilerin bağlantılarını içerir.

## <a name="related-sections"></a>İlgili bölümler
- [Visual Studio geliştirici portalı ile Office geliştirme](https://developer.microsoft.com/office/docs) Teknik makaleler, videolar ve bloglar gibi ek kaynaklar sağlar.

- [Visual Studio merkezi](https://visualstudio.microsoft.com/) Teknik makaleler Visual Studio videolar ve bloglar gibi ek kaynak kaynakları sağlar.

- [MSDN Kitaplığı 'nın Microsoft Office geliştirme bölümü](/previous-versions/office/office-12/bb726434(v=office.12)) MSDN Kitaplığı 'nın çeşitli Office sürümleri (Visual Studio kullanarak Office geliştirmeye özgü değil) için çözümler geliştirme hakkında makaleler ve başvuru belgeleri bulabileceğiniz alanı.

- [Visual Studio 'Da uygulama geliştirme](/previous-versions/h8w79z10(v=vs.140)) Web uygulamaları, XML Web Hizmetleri ve geleneksel istemci uygulamaları tasarlamak, geliştirmek, hatalarını ayıklamak ve dağıtmak için Visual Studio 'Yu nasıl kullanabileceğinizi açıklayan konuların bağlantılarını içerir.

- [Visual Studio 'da .NET Framework programlama](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Visual Basic ve Visual C# ' de .NET Framework ile uygulama geliştirmeyi anlatır.
