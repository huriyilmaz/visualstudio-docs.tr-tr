---
title: Önkoşullar İletişim Kutusu
description: Önkoşullar iletişim kutusu hangi önkoşul bileşenlerinin yüklü olduğunu, nasıl yük olduklarını ve paketlerin hangi sırada yük olduğunu belirtir.
ms.custom: SEO-VS-2020
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78d5f4f00a81fccf573e69797b9d528ee61ffdc5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628581"
---
# <a name="prerequisites-dialog-box"></a>Önkoşullar iletişim kutusu

**Önkoşullar** iletişim kutusu hangi önkoşul bileşenlerinin yüklü olduğunu, nasıl yük olduklarını ve paketlerin hangi sırada yük olduğunu belirtir.

![Visual Studio'de önkoşullar iletişim kutusu](media/prerequisites-dialog-box.png)

İletişim kutusuna erişmek için, **Çözüm Gezgini'de** bir proje düğümü seçin ve ardından **Özellikler'Project**  >  **seçin.** Project **Tasarımcısı göründüğünde** Yayımla sekmesini **ve** ardından Önkoşullar'ı **seçin.** Kurulum projeleri için, **Project** menüsünde Özellikler'e **tıklayın.** Özellik Sayfaları **iletişim kutusu** göründüğünde Önkoşullar'a **tıklayın.**

## <a name="uielement-list"></a>UIElement listesi

|Öğe|Açıklama|
|-------------|-----------------|
|**Önkoşul bileşenlerini yüklemek için kurulum programı oluşturma**|Bağımlılık sırasına göre, uygulamanın Kurulum programına *(Setup.exe*) önkoşul bileşenlerini dahil edin. Varsayılan olarak, bu seçenek seçilidir. Seçiliyse, herhangi bir *Setup.exe* oluşturulmaz.|
|**Hangi önkoşulların yüklerini seçin**|.NET Framework ve C++ çalışma zamanı kitaplıkları gibi bileşenlerin yük isteyip yüklemey kararlarını belirtir.<br /><br />Örneğin, **SQL Server 2012 Express'in** yanındaki onay kutusunu seçerek, Kurulum programının bu bileşenin hedef bilgisayarda yüklü olup olmadığını doğrulaması ve yüklenmemişse yüklemesi gerektiğini belirtirsiniz.<br /><br />Her önkoşul paketi hakkında ayrıntılı bilgi için bkz. [Önkoşul bilgileri.](#prerequisites-information)|
|**Bileşen satıcısının web sitesinden önkoşulları indirme**|Önkoşul bileşenlerinin satıcının web sitesinden yük olacağını belirtir. Bu varsayılan seçenektir.|
|**Önkoşulları uygulamam ile aynı konumdan indirme**|Önkoşul bileşenlerinin uygulamayla aynı konumdan yük olacağını belirtir. Bu, tüm önkoşul paketlerini yayımlama konuma kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
|**Önkoşulları aşağıdaki konumdan indirin**|Önkoşul bileşenlerinin, girersiniz konumdan yük olacağını belirtir. Bir konum seçmek **için Gözat** düğmesini kullanabilirsiniz.|

> [!NOTE]
> Önkoşulların nereye ekli olduğu hakkında bilgi için [bkz. Önyükleyici paketleri oluşturma.](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages)

## <a name="prerequisites-information"></a>Önkoşul bilgileri

Önkoşullar iletişim **kutusunda görünen önkoşul** bileşenleri aşağıdaki listede yer alan bileşenlerden farklı olabilir. Önkoşullar İletişim Kutusunda listelenen **önkoşul** paketleri, iletişim kutusunu ilk kez açsanız otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirsiniz, yeni hedef çerçeveyle eşleşmesi için önkoşulları el ile seçmeniz gerekir.

|Öğe|Açıklama|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Bu paket şunları yüklür:<br /><br /> - .NET Framework 2.0, 3.0 ve 3.5 sürümlerini içerir.<br />- 32 bit (x86) ve 64 bit (x64) işletim sistemlerindeki tüm .NET Framework sürümleri için destek.<br />- Paketle birlikte .NET Framework her sürüm için dil paketleri.<br />- 2.0 .NET Framework 3.0 için hizmet paketleri.<br /><br /> .NET Framework 3.0, Windows Vista'ya ve .NET Framework 3.5 sürümü de Visual Studio. .NET Framework 3.5, 32 bit işletim sistemleri için derlenmiş ve hedef çerçevenin **.NET Framework 3.5** olarak ayarlandı olduğu tüm Visual Basic ve C# projeleri ve 64 bit işletim sistemleri için derlenmiş Visual Basic ve C# projeleri için gereklidir. (IA64 desteklenmiyor.) Visual Basic ve C# projelerinin varsayılan olarak herhangi bir CPU mimarisi için derlenmiş olduğunu unutmayın. Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış](../../ide/visual-studio-multi-targeting-overview.md) [ve 64 bit uygulamalar için önkoşulları dağıtma.](../../deployment/deploying-prerequisites-for-64-bit-applications.md)|
|**Microsoft .NET Framework 4.x**|Bu paket hem x86 .NET Framework x64 platformları için .NET Framework 4.x'i yüklür.|
|**SQL Server 2014 (x64 ve x86) için Microsoft Sistem CLR Türleri**|Bu paket, x64 veya x86 için SQL Server 2014 için Microsoft Sistem CLR Türleri'ne yüklenir.|
|**SQL Server 2008 R2 Express**|Bu paket, Microsoft SQL Server, sunucu veya masaüstü uygulamaları için ideal bir veritabanı olan Microsoft SQL Server 2008 R2 Express'in ücretsiz bir sürümü olan Microsoft SQL Server 2008 R2 Express'i yüklemektedir. Geliştirme ve üretim için ücretsiz olarak kullanılabilir.|
|**SQL Server 2012 Express**|Bu paket, Microsoft SQL Server 2012 Express'i yüklür.|
|**SQL Server 2012 Express LocalDB**|Bu paket, Microsoft SQL Server 2012 Express LocalDB'yi yüklür.|
|**Visual C++ "14" Çalışma Zamanı Kitaplıkları (ARM)**|Bu paket, Microsoft Visual C++ için programlama yordamları sağlayan Itanium mimarisi için çalışma zamanı kitaplıklarını Windows yüklenir. Bu yordamlar, C ve C++ dilleri tarafından sağlanmış olan birçok yaygın programlama görevlerini otomatik hale sunar.<br /><br /> Daha fazla bilgi için [bkz. C Run-Time Kitaplık Başvurusu.](/cpp/c-runtime-library/c-run-time-library-reference)|
|**Visual C++ "14" Çalışma Zamanı Kitaplıkları (x64)**|Bu paket, microsoft Visual C++ programlama yordamları sağlayan x64 işletim sistemleri için çalışma zamanı kitaplıklarını Windows yüklenir. Bu yordamlar, C ve C++ dilleri tarafından sağlanmış olan birçok yaygın programlama görevlerini otomatik hale sunar.<br /><br /> Daha fazla bilgi için [bkz. C Run-Time Kitaplık Başvurusu.](/cpp/c-runtime-library/c-run-time-library-reference)|
|**Visual C++ "14" Çalışma Zamanı Kitaplıkları (x86)**|Bu paket, microsoft Visual C++ için programlama yordamları sağlayan x86 işletim sistemleri için çalışma zamanı kitaplıklarını Windows yüklenir. Bu yordamlar, C ve C++ dilleri tarafından sağlanmış olan birçok yaygın programlama görevlerini otomatik hale sunar.<br /><br /> Daha fazla bilgi için [bkz. C Run-Time Kitaplık Başvurusu.](/cpp/c-runtime-library/c-run-time-library-reference)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yayın Sayfası, Proje Tasarımcısı](../../ide/reference/publish-page-project-designer.md)
- [Uygulama Dağıtımı Önkoşulları](../../deployment/application-deployment-prerequisites.md)
- [64 bit Uygulamalar için Önkoşulları Dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Çerçeve hedeflemeye genel bakış](../../ide/visual-studio-multi-targeting-overview.md)
