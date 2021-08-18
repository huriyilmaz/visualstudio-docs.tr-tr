---
title: .net 4,5 'e geçirilen Office projeleri için gereken değişiklikler
description: hedef çerçeve .NET Framework daha önceki bir sürümünden .NET Framework 4 ' e veya daha sonraki bir sürüme değişirse, projenizde yapmanız gereken değişiklikleri öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8b1e3ca556e07e0d4df8a27142a0700fd40e09a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032231"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>.net 4,5 'e geçirilen Office projeleri için gereken değişiklikler

  bir Office projesinin hedef çatısı, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework önceki bir sürümünden veya daha sonraki bir sürümüyle değiştirilmişse, çözümün geliştirme bilgisayarında ve son kullanıcı bilgisayarlarında çalışmasını sağlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

- <xref:System.Security.SecurityTransparentAttribute>Visual Studio 2008 ' den yükselttiyseniz projeden kaldırın.

- geliştirme bilgisayarında projeyi çalıştırabilmek veya hata ayıklayabilmek için Visual Studio bir **temiz** komut gerçekleştirin.

- projenin .NET Framework önkoşullarını güncelleştirin.

- son kullanıcılar, hedef framework 'ü değiştirmeden önce ClickOnce kullanarak daha önce dağıttıysanız de çözümü yeniden yüklemektir.

  Bu görevlerin her biri hakkında daha fazla bilgi için aşağıdaki ilgili bölümlere bakın.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008 ' den yükselttiğiniz projelerden securitytransparent özniteliğini kaldırın
 bir Office projesini Visual Studio 2008 ' den yükseltiyorsanız ve projenin hedef framework 'ü daha [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonra ya da daha sonra değişirse, projeden kaldırmanız gerekir <xref:System.Security.SecurityTransparentAttribute> . Visual Studio, bu özniteliği sizin için otomatik olarak kaldırmaz. Bu özniteliği kaldırdıysanız, projeyi derlerken bir hata iletisi alırsınız.

 Visual Studio yükseltilen bir projenin hedef çerçevesini veya içine değiştirebileceği koşullar hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , bkz. [Office çözümleri yükseltme ve geçirme](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>SecurityTransparentAttribute 'yi kaldırmak için

1. proje Visual Studio açıkken **Çözüm Gezgini** açın.

2. **özellikler** düğümü (C# için) veya **Project** düğümü altında (Visual Basic için), assemblyınfo kod dosyasına çift tıklayarak kodu düzenleyici 'de açın.

    > [!NOTE]
    > Visual Basic projelerinde, assemblyınfo kod dosyasını görmek için **Çözüm Gezgini** **tüm dosyaları göster** düğmesini tıklamalısınız.

3. Öğesini bulun <xref:System.Security.SecurityTransparentAttribute> ve dosyadan kaldırın ya da not edin.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Geliştirme bilgisayarında hata ayıklamak veya bir projeyi çalıştırmak için Temizle komutunu gerçekleştirme
 projenin hedef çerçevesi veya daha sonraki bir sürüme değiştirilmeden önce bir Office projesi oluşturulduysa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bir **temiz** komut gerçekleştirmeniz ve ardından hedef framework değiştirildikten sonra projeyi yeniden oluşturmanız gerekir. **Temiz** bir komut gerçekleştirmezse, <xref:System.Runtime.InteropServices.COMException> yeniden hedeflenen projeyi hata ayıklamaya veya çalıştırmaya çalıştığınızda bir gönderilir.

 **temizleme** komutu hakkında daha fazla bilgi için bkz. [Build Office solutions](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Dağıtım önkoşullarını güncelleştirme
 bir Office projesini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümüne yeniden hedeflediyseniz, **önkoşullar** iletişim kutusunda ilgili .NET Framework önkoşulu da güncelleştirmeniz gerekir. aksi takdirde, ClickOnce dağıtımı veya ınstallshield Limited Edition projesi .NET Framework önceki bir sürümünü denetler ve kurar.

 son kullanıcı bilgisayarlarına dağıtım önkoşullarını güncelleştirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: son kullanıcı bilgisayarlarına önkoşulları yüklemek Office çözümleri çalıştırma](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Son kullanıcı bilgisayarlarına çözümleri yeniden yükleme
 .NET Framework 3,5 ' i hedefleyen bir Office çözümü dağıtmak için ClickOnce kullanırsanız ve ardından projeyi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürüme yeniden hedeflemeniz durumunda, son kullanıcılar çözümü kaldırmalı ve sonra çözümü yeniden yayınladıktan sonra yeniden yüklemektir. Yeniden hedeflenen çözümü yeniden yayımlarsanız ve çözüm son kullanıcı bilgisayarlarında güncelleştirilirse, son kullanıcılar <xref:System.Runtime.InteropServices.COMException> güncelleştirilmiş çözümü çalıştırırken bir alır.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)