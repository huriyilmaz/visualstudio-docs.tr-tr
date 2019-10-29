---
title: 'Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi'
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 801486e7c0abfa2cb91f7fb7237cf3a48e8bc916
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985913"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi
  Office çalışma zamanı için Visual Studio 2010 araçları, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Microsoft Office geliştirici araçları kullanılarak oluşturulan çözümler çalıştıran her bilgisayarda yüklü olmalıdır. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]yüklediğinizde çalışma zamanı otomatik olarak yüklenir ve Microsoft Office. Daha fazla bilgi için bkz. [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Aşağıdaki durumlarda el ile yükleme yönergelerini izlemeniz gerekebilir:

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sunucuya yüklemeniz gerekir. Örneğin, bir sunucudaki belge düzeyi çözümlerini yönetmek için <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfını kullanmak istiyorsunuz.

- Çalışma zamanını, Office çözümlerinin tüm diğer önkoşullarının zaten yüklü olduğu bir bilgisayara yüklemeniz gerekir.

    > [!NOTE]
    > .NET Framework ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]yüklemek için geliştirme bilgisayarında bir yönetici olmanız gerekir.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı Visual Studio Araçları yüklemek için

1. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üstünü yükler.

    - [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]indirmek için, bkz. [Microsoft .NET Framework 4 (Web Yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17851).

    - [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]indirmek için, bkz. [Microsoft .NET Framework 4 Istemci profili (Web Yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17113).

    - [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]indirmek için, bkz. [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]yüklemek için *vstor_redist. exe dosyasını* çalıştırın.

     Bu kurulum dosyalarını, [Office çalışma zamanı Için Visual Studio 2010 araçlarından](https://www.microsoft.com/download/details.aspx?id=56961)indirebilirsiniz. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] önkoşulları, .NET Framework önkoşulları ile eşleşir.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dil paketleri içerir. Windows yüklemeniz Ingilizce dışında bir dile ayarlandıysa, çalışma zamanı iletilerini Windows için kullandığınız dilde görüntüleyebilirsiniz. Benzer şekilde, son kullanıcılar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yükler ve ardından çözümlerinizi Ingilizce dışındaki bir dile ayarlanmış Windows yüklemelerinde çalıştırırsanız, çalışma zamanı iletileri Windows ile aynı dilde görünür. Bazı durumlarda, ek dil paketlerine ihtiyacınız bulunabilir. Örneğin, Windows kopyanız birden fazla dil ayarı kullanıyorsa veya [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]zaten yüklendikten sonra başka bir dile geçiş yaparsanız, ek dil paketlerine ihtiyacınız vardır. Dil paketlerini [Microsoft Office sistemi (sürüm 4,0 çalışma zamanı) dil paketi için Microsoft Visual Studio 2010 araçlarında](https://www.microsoft.com/download/details.aspx?id=54246)bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio &#40;'da Office geliştirme ile çalışmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
