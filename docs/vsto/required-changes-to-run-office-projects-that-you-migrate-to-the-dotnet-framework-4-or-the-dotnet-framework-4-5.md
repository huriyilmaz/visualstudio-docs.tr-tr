---
title: .NET Framework 4 ' e geçirilen Office projeleri için gereken değişiklikler 4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 773a4dd319d00487b919721bf3390a7d58c8b03c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810973"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office projelerini çalıştırmak için gereken değişiklikler
  Bir Office projesinin hedef çatısı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework önceki bir sürümünden veya daha sonraki bir sürüme değiştirilmişse, çözümün geliştirme bilgisayarında ve son kullanıcı bilgisayarlarında çalışmasını sağlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

- <xref:System.Security.SecurityTransparentAttribute>Projeyi Visual Studio 2008 ' den yükselttiyseniz projeden kaldırın.

- Geliştirme bilgisayarında projeyi çalıştırmak veya hata ayıklamak için Visual Studio 'da bir **temiz** komut gerçekleştirin.

- Projenin .NET Framework önkoşullarını güncelleştirin.

- Hedef Framework 'ü değiştirmeden önce daha önce ClickOnce kullanarak dağıttıysanız, son kullanıcılar da çözümü yeniden yüklemenizi sağlamalıdır.

  Bu görevlerin her biri hakkında daha fazla bilgi için aşağıdaki ilgili bölümlere bakın.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008 ' den yükselttiğiniz projelerden SecurityTransparent özniteliğini kaldırma
 Bir Office projesini Visual Studio 2008 ' den yükseltiyorsanız ve projenin hedef Framework 'ü daha [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonra veya daha sonra olarak değişirse, öğesini projeden kaldırmanız gerekir <xref:System.Security.SecurityTransparentAttribute> . Visual Studio bu özniteliği sizin için otomatik olarak kaldırmaz. Bu özniteliği kaldırdıysanız, projeyi derlerken bir hata iletisi alırsınız.

 Visual Studio 'nun, yükseltilen bir projenin hedef çerçevesini veya sürümüne değiştirebileceği koşullar hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] bkz. [Office çözümlerini yükseltme ve geçirme](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>SecurityTransparentAttribute 'yi kaldırmak için

1. Visual Studio 'da proje açıkken **Çözüm Gezgini**açın.

2. **Özellikler** düğümü (C# için) veya **projem** düğümü altında (Visual Basic Için), AssemblyInfo kod dosyasına çift tıklayarak kodu düzenleyici 'de açın.

    > [!NOTE]
    > Visual Basic projelerinde, AssemblyInfo kod dosyasını görmek için **Çözüm Gezgini** **tüm dosyaları göster** düğmesini tıklamalısınız.

3. Öğesini bulun <xref:System.Security.SecurityTransparentAttribute> ve dosyadan kaldırın ya da not edin.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Geliştirme bilgisayarında hata ayıklamak veya bir projeyi çalıştırmak için Temizle komutunu gerçekleştirme
 Projenin hedef çerçevesi veya daha sonraki bir sürüme değiştirilmeden önce bir Office projesi oluşturulduysa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bir **temiz** komut gerçekleştirmeniz ve ardından hedef Framework değiştirildikten sonra projeyi yeniden oluşturmanız gerekir. **Temiz** bir komut gerçekleştirmezse, <xref:System.Runtime.InteropServices.COMException> yeniden hedeflenen projeyi hata ayıklamaya veya çalıştırmaya çalıştığınızda bir gönderilir.

 **Temizleme** komutu hakkında daha fazla bilgi için bkz. [Build Office Solutions](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Dağıtım önkoşullarını güncelleştirme
 Office projesini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha yeni bir sürümüne yeniden hedeflediğinizde, **Önkoşullar** iletişim kutusunda karşılık gelen .NET Framework önkoşulu da güncelleştirmeniz gerekir. Aksi takdirde, ClickOnce dağıtımı veya InstallShield Limited Edition projesi .NET Framework önceki bir sürümünü denetler ve kurar.

 Son kullanıcı bilgisayarlarına dağıtım önkoşullarını güncelleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarına önkoşulları yüklemek](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Son kullanıcı bilgisayarlarına çözümleri yeniden yükleme
 .NET Framework 3,5 ' i hedefleyen bir Office çözümünü dağıtmak için ClickOnce kullanırsanız ve ardından projeyi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümüne yeniden hedeflemeniz durumunda, son kullanıcılar çözümü kaldırmalı ve sonra çözümü yeniden yayınladıktan sonra yeniden yüklemektir. Yeniden hedeflenen çözümü yeniden yayımlarsanız ve çözüm son kullanıcı bilgisayarlarında güncelleştirilirse, son kullanıcılar <xref:System.Runtime.InteropServices.COMException> güncelleştirilmiş çözümü çalıştırırken bir alır.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)