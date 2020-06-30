---
title: 'Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi'
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef71de75be5977ab80cbdd85448daa5de381c077
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547231"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi
  Office çalışma zamanı için Visual Studio 2010 araçları, ' de Microsoft Office geliştirici araçları kullanılarak oluşturulan çözümler çalıştıran her bilgisayara yüklenmelidir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Çalışma zamanı, yüklediğinizde ve Microsoft Office otomatik olarak yüklenir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Aşağıdaki durumlarda el ile yükleme yönergelerini izlemeniz gerekebilir:

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]' Nı bir sunucusuna yüklemeniz gerekir. Örneğin, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> bir sunucudaki belge düzeyi çözümlerini yönetmek için sınıfını kullanmak istiyorsunuz.

- Çalışma zamanını, Office çözümlerinin tüm diğer önkoşullarının zaten yüklü olduğu bir bilgisayara yüklemeniz gerekir.

    > [!NOTE]
    > .NET Framework ve ' ü yüklemek için geliştirme bilgisayarında bir yönetici olmanız gerekir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı Visual Studio Araçları yüklemek için

1. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya sonraki sürümünü yükler.

    - İndirmek için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bkz. [Microsoft .NET Framework 4 (Web Yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17851).

    - İndirmek için [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] , bkz. [Microsoft .NET Framework 4 istemci profili (Web Yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17113).

    - İndirmek için [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , bkz. [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Uygulamasını yüklemek için *vstor_redist.exe* çalıştırın [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     Bu kurulum dosyalarını, [Office çalışma zamanı Için Visual Studio 2010 araçlarından](https://www.microsoft.com/download/details.aspx?id=56961)indirebilirsiniz. İçin önkoşulları, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .NET Framework önkoşulları ile eşleşir.

     , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Dil paketlerini içerir. Windows yüklemeniz Ingilizce dışında bir dile ayarlandıysa, çalışma zamanı iletilerini Windows için kullandığınız dilde görüntüleyebilirsiniz. Benzer şekilde, son kullanıcılar ürününü yüklerse [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve sonra, İngilizce dışındaki bir dile ayarlanmış Windows yüklemelerinde çözümlerinizi çalıştırırsanız, çalışma zamanı Iletileri Windows ile aynı dilde görünür. Bazı durumlarda, ek dil paketlerine ihtiyacınız bulunabilir. Örneğin, Windows kopyanız birden fazla dil ayarı kullanıyorsa veya daha önce yükledikten sonra başka bir dile geçiş yaparsanız, ek dil paketlerine ihtiyaç duyabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Dil paketlerini [Microsoft Office sistemi (sürüm 4,0 çalışma zamanı) dil paketi için Microsoft Visual Studio 2010 araçlarında](https://www.microsoft.com/download/details.aspx?id=54246)bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
