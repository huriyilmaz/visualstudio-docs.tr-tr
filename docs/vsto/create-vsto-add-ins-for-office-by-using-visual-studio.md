---
title: Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
description: Visual Studio'daki Microsoft Office geliştirici araçlarını kullanarak .NET Framework uygulamaları Office.
titleSuffix: ''
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
ms.openlocfilehash: cd6f60c9af5a352b0c432d96fa731112987a1d96
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971094"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Visual Studio kullanarak Office için VSTO Eklentileri oluşturma
> [!IMPORTANT]
> VSTO, [.NET Framework.](/dotnet/framework/get-started/overview) COM eklentileri, .NET Framework. Office Eklentiler, .NET Core ve [.NET 5+](/dotnet/core/dotnet-five)ile oluşturulamaz. Bu, .NET'in en son sürümleridir. Bunun nedeni.NET Core/.NET 5+ ile aynı işlemde .NET Framework birlikte çalışamaz ve eklenti yük hatalarına yol açabilir. .NET Framework için VSTO com eklentilerini yazmaya devam Office. Microsoft, .NET Core VSTO .NET 5+ kullanmak için VSTO com eklenti platformunu güncelleştirmez. Web Eklentileri'nin sunucu tarafını oluşturmak için .NET Core ve .NET 5+ ASP.NET Core da dahil [olmak üzere Office kullanabilirsiniz.](/office/dev/add-ins/overview/office-add-ins)

  Visual Studio'daki Microsoft Office geliştirici araçlarını kullanarak .NET Framework uygulamaları Office. Bu uygulamalar, çözüm olarak *Office adlandırılmıştır.*

 Bu Office araçları, çeşitli iş ihtiyaçlarına uygun Office çözümler oluşturmanıza yardımcı olan özellikler sağlar. Araçlar, Visual Basic veya Visual C# kullanarak Office çözümleri oluşturmanıza yardımcı olacak proje şablonlarını ve Office çözümleriniz için özel kullanıcı arabirimleri oluşturmanıza yardımcı olan görsel tasarımcıları içerir.

[!include[Add-ins note](includes/addinsnote.md)]

 Geliştirme hakkında en son Office için bkz. [Microsoft Office merkezi.](https://developer.microsoft.com/office/docs)

## <a name="in-this-section"></a>Bu bölümde
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Geliştirme bilgisayarlarını Office çözümleri oluşturmak üzere yapılandırma, Office çözümleri oluşturmaya başlama ve geliştirme aşamasında Office için Visual Studio.

- [Çözümlerini yükseltme Office geçirme](upgrading-and-migrating-office-solutions.md)

 Önceki sürümler kullanılarak oluşturulan projelerin yükseltme işlemiyle ilgili bilgilerin bağlantılarını Visual Studio.

- [Visual Studio'Office çözümlerinin mimarisi](architecture-of-office-solutions-in-visual-studio.md)

 Belge düzeyi özelleştirmeler ve Office hakkında bilgiler de dahil olmak üzere, çözüm çözümlerinin nasıl VSTO bağlantılar sağlar.

- [Yeni çözümler tasarlama Office oluşturma](designing-and-creating-office-solutions.md)

 Yeni bir proje oluşturma ve Office yapılandırma hakkında bilgi Visual Studio.

- [Yeni Office geliştirme](developing-office-solutions.md)

 Yönetilen kodun kullanıcı arabirimini özelleştirme, verilerle Office ve sorunları giderme dahil olmak üzere Office çözümlerini kullanma hakkında bilgi sağlar.

- [Excel çözümleri](excel-solutions.md)

 Bu hizmetleri otomatikleştirme, Excel çözümleri Excel ve Excel'a özgü genelleştirme sorunlarını anlama hakkında bilgi Excel.

- [InfoPath çözümleri](infopath-solutions.md)

 InfoPath için form şablonları oluşturma ve VSTO hakkında bilgi sağlar.

- [Outlook çözümleri](outlook-solutions.md)

 Eklentileri ve form bölgelerini otomatik Outlook ve Outlook VSTO oluşturma hakkında bilgi sağlar.

- [PowerPoint çözümleri](powerpoint-solutions.md)

 Eklentileri otomatikleştirme ve PowerPoint oluşturma hakkında PowerPoint VSTO bilgi sağlar.

- [Project çözümleri](project-solutions.md)

 Uygulama projesini otomatikleştirme ve Microsoft Office oluşturma hakkında VSTO bilgi sağlar.

- [Visio çözümleri](visio-solutions.md)

 Eklentileri otomatikleştirme ve Visio oluşturma hakkında Visio VSTO bilgi sağlar.

- [Sözcük çözümleri](word-solutions.md)

 Word'leri otomatikleştirme ve Word çözümleri oluşturma hakkında bilgi sağlar.

- [Yeni Office oluşturma](building-office-solutions.md)

 Uygulama projeleri ve 'de Office proje türleri arasındaki farklar hakkında bilgi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlar.

- [Projelerde Office ayıklama](debugging-office-projects.md)

 Projelerde ve 'daki diğer proje Office hata ayıklama arasındaki farklar hakkında bilgi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlar.

- [Güvenli Office çözümleri](securing-office-solutions.md)

 Güvenlik özelliklerinin farklı çözümlerde nasıl Office sağlar.

- [Bir Office dağıtma](deploying-an-office-solution.md)

 Uygulama çözümlerinin kullanıcılarınız Office ve dağıtım yöntemi seçtiğiniz zaman dikkate alınan başlıca sorunlar hakkında bilgi sağlar.

- [Office örnekleri ve izlenecek yollar](office-development-samples-and-walkthroughs.md)

 Genel görevleri gerçekleştirmeye ilişkin adım adım yönergeler sağlayan örnek uygulamalara ve konulara bağlantılar sağlar.

- [Geliştirme aşamasında &#40;Office başvuru Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Birincil birlikte çalışma derlemeleri, Office, kullanıcı arabirimi öğeleri ve hata iletileri hakkında ayrıntılı bilgilere bağlantılar sağlar.

- [Visual Studio&#41;'&#40;Office yönetilen başvuru Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 hedef projelerinde kullanılan API ad alanları ve türleri hakkında Office bağlantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sağlar. .NET Framework 3.5'i hedef alan Office projelerinde kullanılan ad alanları ve türleri hakkında API başvurusu belgeleri için Visual Studio 2008 belgelerinde aşağıdaki başvuru bölümüne [bakın: 2007](managed-reference-office-development-in-visual-studio.md)sistem tarafından yönetilen başvuru.

- [Visual Studio&#41;'de &#40;Office API başvurusu Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Office uygulamalarına yönetilen eklenti yükleme ve kaldırma gibi eylemleri gerçekleştirmek için kullanabileceğiniz COM arabirimleri hakkında VSTO bağlantıları içerir.

## <a name="related-sections"></a>İlgili bölümler
- [Office portal ile Visual Studio geliştirme](https://developer.microsoft.com/office/docs) Teknik makaleler, videolar ve bloglar gibi ek kaynaklar sağlar.

- [Visual Studio merkezi](https://visualstudio.microsoft.com/) Teknik makaleler, Visual Studio bloglar gibi ek kaynak kaynakları sağlar.

- [Microsoft Office msdn kitaplığının geliştirme bölümü](/previous-versions/office/office-12/bb726434(v=office.12)) MSDN kitaplığının çeşitli sürümlerine yönelik çözümler geliştirmeyle ilgili makaleler ve başvuru belgelerinin bulunduğu Office (Office kullanarak geliştirme Visual Studio).

- [Visual Studio'de uygulama geliştirme](/previous-versions/h8w79z10(v=vs.140)) Web uygulamaları, XML web hizmetleri ve geleneksel istemci Visual Studio tasarlamak, geliştirmek, hata ayıklamak ve dağıtmak için Visual Studio'yi nasıl kullanabileceğiniz hakkında bilgi içeren konuların bağlantılarını içerir.

- [.NET Framework programlama Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Visual Basic ve Visual C# .NET Framework uygulama geliştirmeyi ele alan.
