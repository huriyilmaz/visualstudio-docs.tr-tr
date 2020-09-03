---
title: Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 507bce496405f615343a9c109ff71196d814af08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64800184"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları
  Office çalışma zamanı için Visual Studio 2010 araçları 'nı üç şekilde yükleyebilirsiniz:

- Visual Studio 'Yu yüklediğinizde.

- Microsoft Office yüklediğinizde.

- Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 araçları 'nı yüklediğinizde.

  Yüklü çalışma zamanı bileşenleri bilgisayarın yapılandırmasına ve yükleme senaryosuna bağlıdır.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Her yükleme senaryosunda yüklü çalışma zamanı bileşenleri
 Office çalışma zamanı için Visual Studio 2010 araçları 'nın üç bileşeni vardır: Office çözüm yükleyicisi, .NET Framework 3,5 için Office uzantıları ve veya üzeri için Office uzantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Çalışma zamanını yüklerken Office çözüm yükleyicisi her zaman yüklenir. .NET Framework için Office uzantılarının yüklemesi bilgisayarın yapılandırmasına ve yükleme senaryosuna bağlıdır. Çalışma zamanı ilk yüklendiğinde Office uzantılarından biri yüklenemezse, belirli gereksinimler karşılandığında çalışma zamanı eksik Office uzantılarını otomatik olarak yükler. Çalışma zamanının bu özelliğine *istek üzerine Install*adı verilir.

 Aşağıdaki tabloda, her çalışma zamanı yükleme senaryosunda varsayılan olarak hangi çalışma zamanı bileşenlerinin yüklendiği gösterilmektedir. Her senaryo hakkında daha fazla bilgi daha sonra görünür.

|Çalışma zamanı yükleme senaryosu|Office çözüm yükleyicisi|.NET Framework 3,5 için Office uzantıları|İçin Office uzantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|İçin Office uzantıları [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]Ve sonraki sürümlerde|Evet|Evet, .NET Framework 3,5 zaten yüklüyse.|Evet|Evet|
|Kullanılarak [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Evet|Evet, .NET Framework 3,5 zaten yüklüyse.|Hayır|Hayır|
|Office 2010 Service Pack 1 (SP1) veya üzeri ile|Evet|Evet, .NET Framework 3,5 zaten yüklüyse.|Evet, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklüyse.|Hayır|
|Yeniden dağıtılabilir çalışma zamanı|Evet|Evet, .NET Framework 3,5 zaten yüklüyse|Evet, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] zaten yüklüyse.|Evet, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] zaten yüklüyse.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Visual Studio veya Visual Studio için Microsoft Office Geliştirici Araçları çalışma zamanını yükler
 Visual Studio 'da Office geliştirici araçları 'nı yüklediğinizde, ve için Office uzantıları [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] her zaman geliştirme bilgisayarında yüklüdür. 3,5 .NET Framework için Office uzantıları, yalnızca geliştirme bilgisayarında .NET Framework 3,5 zaten mevcutsa yüklenir. Yükledikten sonra 3,5 .NET Framework yüklerseniz [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , çalışma zamanı .NET Framework 3,5 ' i hedefleyen bir Office projesi oluşturduğunuzda, .NET Framework 3,5 Için Office uzantılarını otomatik olarak yükler.

> [!WARNING]
> Veya sonraki sürümlerini kullanarak .NET Framework 3,5 ' i hedefleyen bir Office projesi oluşturamazsınız [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Office Geliştirici araçlarının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: bilgisayarı yapılandırma Office çözümleri geliştirme](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Office ile çalışma zamanını yükler
 Office 'i yüklediğinizde, bilgisayarda .NET Framework 3,5 zaten varsa .NET Framework 3,5 Office uzantıları yüklenir. .NET Framework 3,5 ' yi Office sonrasında yüklerseniz, bir Office uygulaması .NET Framework 3,5 ' i hedefleyen bir çözümü yüklemeye çalıştığında, çalışma zamanı .NET Framework 3,5 için Office uzantılarını otomatik olarak yükler.

 Office 'i [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklediğinizde veya daha sonra zaten mevcut olsa bile, veya üzeri Office uzantıları Office ile yüklenmez.

 Office uzantıları [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office ile yüklenir. Son kullanıcılar Windows Update yükleyerek için Office uzantıları edinebilir [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] .

 Kullanıcılarınızın uygulamanızı kullanmak için gerekli uzantılara sahip olduğundan emin olmak için, Office çalışma zamanı için Visual Studio 2010 Araçları ' nın en son sürümünü çözümünüz için bir önkoşul olarak ekleyin. Önkoşullar hakkında daha fazla bilgi için bkz. [dağıtım Için Office çözüm önkoşulları](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Çalışma zamanını yeniden dağıtılabilir kullanarak yükler
 Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 araçları 'nı el ile çalıştırarak veya bir Office çözümünü dağıtırken yeniden dağıtılabilir bir önkoşul olarak ekleyerek çalışma zamanını yükleyebilirsiniz.

 Çalışma zamanını Office çalışma zamanı yeniden dağıtılabilir için Visual Studio 2010 Araçları ' nı kullanarak yüklediğinizde, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework ilgili sürümleri bilgisayarda zaten mevcutsa, 3,5 .NET Framework Için Office uzantıları ve veya üzeri Için Office uzantıları yüklenir. Çalışma zamanı yüklenirken bilgisayarda bu .NET Framework sürümlerinden biri eksikse, .NET Framework eksik sürümüne ait Office uzantıları o anda yüklenmez. .NET Framework eksik sürümünü daha sonra yüklerseniz, uzantıları gerektiren bir çözüm yüklendiğinde (çalışma zamanı ClickOnce kullanılarak dağıtılan bir çözümle birlikte yüklendiyse) veya yüklü (çalışma zamanı Windows Installer kullanılarak dağıtılan bir çözümle yüklenmişse), çalışma zamanı ilgili Office uzantılarını otomatik olarak yükler.

 ClickOnce çözümüne önkoşulları ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: son kullanıcı bilgisayarlarına önkoşulları yüklemek Için Office çözümlerini çalıştırın](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Yeniden dağıtılabilir paketten çalışma zamanının el ile nasıl yükleneceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Office çalışma zamanı için Visual Studio Araçları derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
