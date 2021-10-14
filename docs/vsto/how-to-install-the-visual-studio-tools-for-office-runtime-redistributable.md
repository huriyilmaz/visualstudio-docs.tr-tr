---
title: 'nasıl yapılır: Office için Visual Studio Araçları çalışma zamanı yeniden dağıtılabilir'
description: Office çalışma zamanı yeniden dağıtılabilir için Microsoft Visual Studio 2010 araçlarını nasıl yükleyebileceğinizi öğrenin.
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 90d5f6fd584f597e6022310fe305a546654a3886
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970990"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>nasıl yapılır: Office için Visual Studio Araçları çalışma zamanı yeniden dağıtılabilir
  Office çalışma zamanı için Visual Studio 2010 araçları, içindeki Microsoft Office geliştirici araçları kullanılarak oluşturulan çözümler çalıştıran her bilgisayarda yüklü olmalıdır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Çalışma zamanı, yüklediğinizde ve Microsoft Office otomatik olarak yüklenir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . daha fazla bilgi için bkz. [Office için Visual Studio Araçları runtime yükleme senaryoları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Aşağıdaki durumlarda el ile yükleme yönergelerini izlemeniz gerekebilir:

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]' Nı bir sunucusuna yüklemeniz gerekir. Örneğin, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> bir sunucudaki belge düzeyi çözümlerini yönetmek için sınıfını kullanmak istiyorsunuz.

- çalışma zamanını, Office çözümleri için diğer tüm önkoşulların zaten yüklü olduğu bir bilgisayara yüklemeniz gerekir.

    > [!NOTE]
    > .NET Framework ve ' ü yüklemek için geliştirme bilgisayarında bir yönetici olmanız gerekir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları çalışma zamanını yüklemek için

1. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya sonraki sürümünü yükler.

    - indirmek için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] bkz. [Microsoft .NET Framework 4 (Web yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17851).

    - indirmek için [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] bkz. [Microsoft .NET Framework 4 istemci profili (Web yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17113).

    - indirmek için [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] bkz. [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Uygulamasını yüklemek için *vstor_redist.exe* çalıştırın [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     bu kurulum dosyalarını, [Office çalışma zamanına yönelik Visual Studio 2010 araçlarından](https://www.microsoft.com/download/details.aspx?id=56961)indirebilirsiniz. İçin önkoşulları, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .NET Framework önkoşulları ile eşleşir.

     , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Dil paketlerini içerir. Windows yüklemeniz ingilizce dışında bir dile ayarlandıysa, çalışma zamanı iletilerini Windows kullandığınız dilde görüntüleyebilirsiniz. benzer şekilde, son kullanıcılar uygulamasını yüklerse [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve sonra, ingilizce dışında bir dile ayarlanmış Windows yüklemelerine yüklüyorsanız, çalışma zamanı iletileri Windows aynı dilde görünür. Bazı durumlarda, ek dil paketlerine ihtiyacınız bulunabilir. örneğin, Windows kopyanız birden fazla dil ayarı kullanıyorsa veya daha önce yükledikten sonra başka bir dile geçiş yaparsanız, ek dil paketlerine ihtiyaç duyabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . dil paketlerini [Microsoft Office sistemi (sürüm 4,0 çalışma zamanı) dil paketi için Microsoft Visual Studio 2010 araçlarında](https://www.microsoft.com/download/details.aspx?id=54246)bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [nasıl yapılır: birincil birlikte çalışma derlemelerini Office yüklemesi](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
