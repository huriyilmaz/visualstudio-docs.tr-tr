---
title: 'Nasıl kurulur: Office için Visual Studio Araçları çalışma zamanı yeniden dağıtılabilir yükleme'
description: Çalışma zamanı yeniden dağıtılabilir için Microsoft Visual Studio 2010 Araçları'Office nasıl yükleyebilirsiniz?
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
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
ms.openlocfilehash: c9c74cd354f89725352c5c8b22557956fcd9624c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083485"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Nasıl kurulur: Office için Visual Studio Araçları çalışma zamanı yeniden dağıtılabilir yükleme
  Office için Visual Studio 2010 Araçları' Office,'daki geliştirici araçları kullanılarak oluşturulan çözümlerin çalıştırılan her bilgisayara Microsoft Office [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gerekir. çalışma zamanı, ve yüklerini [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yükley0000000000000000000000000 Microsoft Office 00000000000000000 Daha fazla bilgi için [bkz. Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları.](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)

[!include[Add-ins note](includes/addinsnote.md)]

 Aşağıdaki durumlarda aşağıdaki el ile yükleme yönergelerini izlemelisiniz:

- bir sunucuya [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklemeniz gerekir. Örneğin, bir sunucu üzerinde belge <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> düzeyi çözümleri yönetmek için sınıfını kullanmak istiyor.

- Çalışma zamanının, tüm diğer önkoşulları zaten yüklü olan bir bilgisayara Office gerekir.

    > [!NOTE]
    > Geliştirme bilgisayarına ve 'i yüklemek için .NET Framework [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gerekir.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları çalışma Office için Visual Studio Araçları yükleme

1. veya sonraki [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] bir sürümü yükleyin.

    - 'i indirmek [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] için [bkz. Microsoft .NET Framework 4 (Web Yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17851).

    - 'i indirmek [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] için [bkz. Microsoft .NET Framework 4 İstemci Profili (Web Yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17113).

    - 'i indirmek için [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [bkz. Microsoft .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653).

2. yüklemek *vstor_redist.exe* için aşağıdakini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çalıştırın.

     Bu kurulum dosyalarını çalışma zamanı için [Visual Studio 2010 Araçları'Office indirebilirsiniz.](https://www.microsoft.com/download/details.aspx?id=56961) önkoşulları, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] uygulamanın önkoşulları .NET Framework.

     , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dil paketlerini içerir. Çalışma zamanı Windows İngilizce dışında bir dile ayarlanırsa, çalışma zamanı iletilerini çalışma zamanı iletilerinizi, çalışma zamanı iletilerinizi Windows. Benzer şekilde, son kullanıcılar İngilizce dışında bir dile ayarlanmış Windows yüklemeleri üzerinde çözümlerinizi çalıştıracaksa, çalışma zamanı iletileri ile aynı dilde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Windows. Bazı durumlarda, ek dil paketlerine ihtiyacınız olabilir. Örneğin, Windows kopyanız birden fazla dil ayarı kullanıyorsa veya 'i yükledikten sonra başka bir dile geçiş yaptıysanız ek dil paketlerine ihtiyacınız [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] olabilir. dil paketlerini, Microsoft Office [(sürüm 4.0 çalışma zamanı) dil paketi için Microsoft Visual Studio 2010 Araçları'nda bulabilirsiniz.](https://www.microsoft.com/download/details.aspx?id=54246)

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Yeni çözümler geliştirmek için bilgisayarı Office yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Nasıl yapılandırılır: Bir bilgisayarı bir bilgisayar için Office yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Nasıl kurulur: Birincil birlikte Office derlemelerini yükleme](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
