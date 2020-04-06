---
title: Kurulumdan Sonra Çalıştırılması Gereken Komutlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709480"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yüklemeden sonra çalıştırılması gereken komutlar
Uzantınızı *.msi* dosyası üzerinden dağıtırsanız, Visual Studio'nun uzantılarınızı keşfetmesi için yüklemenizin bir parçası olarak **devenv /kurulum** çalıştırmanız gerekir.

> [!NOTE]
> Bu konudaki bilgiler Visual Studio 2008 ve daha önce *devenv.exe* bulmak için geçerlidir. Visual Studio'nun sonraki sürümleriyle *devenv.exe'yi* nasıl keşfeden hakkında bilgi [için](../../extensibility/internals/detecting-system-requirements.md)bkz.

## <a name="find-devenvexe"></a>devenv.exe bul
 Kayıt defteri değerlerini özellik olarak depolamak için RegLocator tablosunu ve AppSearch tablolarını kullanarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yükleyicilerin yazdığı kayıt defteri değerlerinden her sürümün *devenv.exe'sini* bulabilirsiniz. Daha fazla bilgi için [bkz.](../../extensibility/internals/detecting-system-requirements.md)

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Visual Studio'nun farklı sürümlerinden devenv.exe'yi bulmak için RegLocator tablo satırları

|İmza|Root|Anahtar|Adı|Tür|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|YAZILIM\Microsoft\VisualStudio\7.0\Setup\VS|Çevre Yolu|2|
|RL_DevenvExe_2003|2|YAZILIM\Microsoft\VisualStudio\7.1\Kurulum\VS|Çevre Yolu|2|
|RL_DevenvExe_2005|2|YAZILIM\Microsoft\VisualStudio\8.0\Setup\VS|Çevre Yolu|2|
|RL_DevenvExe_2008|2|YAZILIM\Microsoft\VisualStudio\9.0\Setup\VS|Çevre Yolu|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>İlgili RegLocator tablo satırları için AppArama tablosu satırları

|Özellik|İmza|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Örneğin, Visual Studio **yükleyiciHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** *olarak C:\VS2008\Common7\IDE\devenv.exe,* yükleyici çalışması gereken yürütülebilir tam bir yol kayıt defteri değeri yazar.

> [!NOTE]
> RegLocator tablosunun Tür sütunu 2 olduğundan, İmza tablosunda ek sürüm bilgileri belirtmeniz gerekmez.

## <a name="run-devenvexe"></a>Çalıştır devenv.exe
 AppSearch standart eylem yükleyici de çalıştırDıktan sonra, AppSearch tablosunda her özellik Visual Studio ilgili sürümü için *devenv.exe* dosyasını gösteren bir değere sahiptir. Belirtilen kayıt defteri değerlerinden herhangi biri yoksa - Visual Studio'nun bu sürümü yüklü olmadığından - belirtilen özellik geçersiz kılınacak şekilde ayarlanır.

 Windows Installer, özel eylem türü 50 ile bir özelliğiişaretleyen bir yürütülebilir çalıştırmayı destekler. Özel eylem, `msidbCustomActionTypeInScript` VSPackage'ın `msidbCustomActionTypeCommit` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]'e entegre edilmeden önce başarıyla yüklendiğinden emin olmak için komut dosyası içi yürütme seçeneklerini (1024) ve (512) içermelidir. Daha fazla bilgi için [CustomAction tablosuna](/windows/desktop/msi/customaction-table) ve [Özel eylem komut dosyası içi yürütme seçeneklerine](/windows/desktop/msi/custom-action-in-script-execution-options)bakın.

 Type 50'nin özel eylemleri, Yürütülebilir özelliği içeren özelliği Hedef sütundaki Kaynak sütunve komut satırı bağımsız değişkenlerinin değeri olarak belirtir.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Devenv.exe çalıştırmak için CustomAction tablo satırları

|Eylem|Tür|Kaynak|Hedef|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/kurulum|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/kurulum|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/kurulum|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/kurulum|

 Yükleme sırasında yürütülmesi için zamanlamak için InstallExecuteSequence tablosuna özel eylemler yazılmalıdır. Bu sürüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sistemde yüklü değilse, özel eylemin çalıştırılmasını önlemek için Durum sütununun her satırındaki ilgili özelliği kullanın.

> [!NOTE]
> Null değerli özellikleri koşullarda `False` kullanıldığında değerlendirir.

 Her özel eylem için Sıra sütununun değeri, Windows Yükleyici paketinizdeki diğer sıra değerlerine bağlıdır. Sıra değerleri, *devenv.exe* özel eylemlerinin InstallFinalize standart eyleminden hemen önce mümkün olduğunca yakın çalışması gibi olmalıdır.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv.exe özel eylemleri zamanlamak için InstallExecuteSequence tablosu

|Eylem|Koşul|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile VSPackages yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
