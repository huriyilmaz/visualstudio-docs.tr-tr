---
title: Yüklemeden sonra çalıştırılması gereken komutlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825178"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yükleme Sonrasında çalıştırılması Gereken Komutlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uzantınızı bir. msi dosyası aracılığıyla dağıtırsanız, `devenv /setup` Visual Studio 'nun uzantılarınızı bulması için yüklemenizin bir parçası olarak çalıştırmanız gerekir.  
  
> [!NOTE]
> Bu konudaki bilgiler, Visual Studio 2008 ve öncesiyle DevEnv bulma için geçerlidir. Visual Studio 'nun sonraki sürümleriyle DevEnv bulma hakkında daha fazla bilgi için bkz. [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>devenv.exe bulma  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kayıt defteri değerlerini özellikler olarak depolamak Için RegLocator tablosu ve AppSearch tablosunu kullanarak her bir sürümün devenv.exe kayıt defteri değerlerinden konumunu bulabilirsiniz. Daha fazla bilgi için bkz. [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Visual Studio 'nun farklı sürümlerindeki devenv.exe bulmak için RegLocator tablo satırları  
  
|Signature_|Root|Anahtar|Ad|Tür|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|Software\microsoft\visualstudio\7,1\setup\vs|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Karşılık gelen RegLocator tablo satırları için AppSearch Tablo satırları  
  
|Özellik|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Örneğin, Visual Studio yükleyicisi **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** kayıt defteri değerini **C:\VS2008\Common7\IDE\devenv.exe**olarak yazar ve yükleyicinin çalıştırması gereken yürütülebilir dosyanın tüm yolu.  
  
 **Göz önünde** RegLocator türü sütunu 2 olduğundan, Imza tablosunda ek sürüm bilgisi belirtilmesi gerekli değildir.  
  
## <a name="running-devenvexe"></a>devenv.exe çalışıyor  
 AppSearch standart eylemi yükleyicide çalıştıktan sonra, AppSearch tablosundaki her bir özellik, ilgili Visual Studio sürümü için devenv.exe dosyasına işaret eden bir değere sahiptir. Belirtilen kayıt defteri değerlerinden herhangi biri mevcut değilse — Visual Studio 'nun bu sürümü yüklü olmadığından, belirtilen özellik null olarak ayarlanır.  
  
 Windows Installer, özelliğin özel eylem türü 50 aracılığıyla işaret ettiği yürütülebilir dosyayı çalıştırmayı destekler. Özel eylem, VSPackage 'ın ile tümleştirmadan önce başarılı bir şekilde yüklendiğinden emin olmak için komut dosyası yürütme seçenekleri, msidbCustomActionTypeInScript (1024) ve msidbCustomActionTypeCommit (512) içermelidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. komut dosyası yürütme seçeneklerinde CustomAction tablosu ve özel eylem.  
  
 50 türündeki özel eylemler, kaynak sütunun değeri olarak yürütülebilir dosyayı içeren özelliği ve hedef sütununda komut satırı bağımsız değişkenlerini belirtir.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>devenv.exe çalıştırılacak CustomAction tablosu satırları  
  
|Eylem|Tür|Kaynak|Hedef|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Yükleme sırasında yürütülmek üzere zamanlamak için, özel eylemler InstallExecuteSequence tablosuna yazılmalıdır. Bu sürümü sistemde yüklü değilse özel eylemin çalıştırılmasını engellemek için koşul sütununun her satırında karşılık gelen özelliğini kullanın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> `Null` Özellikler `False` , koşullarda kullanıldığında olarak değerlendirilir.  
  
 Her bir özel eylem için dizi sütununun değeri, Windows Installer paketinizin diğer sıra değerlerine bağlıdır. Sıra değerleri, devenv.exe özel eylemlerin, InstallFinalize standart eyleminden hemen önce mümkün olduğunca yakın şekilde çalışmasını sağlamalıdır.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>devenv.exe özel eylemleri zamanlamak için InstallExecuteSequence tablosu  
  
|Eylem|Koşul|Sequence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
