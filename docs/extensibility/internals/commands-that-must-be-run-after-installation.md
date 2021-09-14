---
title: Yüklemeden sonra çalıştırılması gereken komutlar | Microsoft Docs
description: Visual Studio bir .msi dosyası aracılığıyla dağıtılan bir uzantı yüklemenizin parçası olarak çalıştırılması gereken komutlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5659c2adbe3b7d8f74ccf0a3a28feefdd7d9421c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725088"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yüklemeden sonra çalıştırılması gereken komutlar
uzantınızı bir *.msi* dosyası aracılığıyla dağıtırsanız, **devenv/setup** ' ı yüklemenizin bir parçası olarak çalıştırmanız gerekir ve bu, uzantılarınızı keşfetmesi için Visual Studio.

> [!NOTE]
> bu konudaki bilgiler, Visual Studio 2008 ve önceki sürümlerde *devenv.exe* bulmak için geçerlidir. daha sonraki Visual Studio sürümleriyle *devenv.exe* bulma hakkında daha fazla bilgi için bkz. [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>devenv.exe bul
 Her sürümün *devenv.exe* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , kayıt defteri değerlerini özellikler olarak depolamak için RegLocator tablosu ve AppSearch tablolarını kullanarak, yükleyiciler tarafından yazılan kayıt defteri değerlerinden bulabilirsiniz. Daha fazla bilgi için bkz. [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Farklı Visual Studio sürümlerinden devenv.exe bulmak için RegLocator tablo satırları

|İmza|Root|Anahtar|Ad|Tür|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|Software\microsoft\visualstudio\7,1\setup\vs|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Karşılık gelen RegLocator tablo satırları için AppSearch Tablo satırları

|Özellik|İmza|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 örneğin, Visual Studio yükleyicisi **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** kayıt defteri değerini *C:\VS2008\Common7\IDE\devenv.exe* olarak yazar ve yükleyicinin çalıştırması gereken yürütülebilir dosyanın tamamına yönelik bir yoldur.

> [!NOTE]
> RegLocator tablosunun Type sütunu 2 olduğundan, Imza tablosunda ek sürüm bilgisi belirtilmesi gerekli değildir.

## <a name="run-devenvexe"></a>devenv.exe Çalıştır
 AppSearch standart eylemi yükleyicide çalıştıktan sonra, AppSearch tablosundaki her bir özelliğin ilgili Visual Studio *devenv.exe* dosyasına işaret eden bir değeri vardır. belirtilen kayıt defteri değerlerinden herhangi biri mevcut değilse — Visual Studio sürümü yüklü olmadığından, belirtilen özellik null olarak ayarlanır.

 Windows Yükleyici, bir özelliğin, 50 özel eylem türü aracılığıyla işaret ettiği bir yürütülebiliri çalıştırmayı destekler. Özel eylem, `msidbCustomActionTypeInScript` `msidbCustomActionTypeCommit` VSPackage 'ın ile tümleştirmadan önce başarılı bir şekilde yüklendiğinden emin olmak için komut dosyası yürütme seçeneklerini (1024) ve (512) içermelidir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. [komut dosyası yürütme seçeneklerinde](/windows/desktop/msi/custom-action-in-script-execution-options) [CustomAction tablosu](/windows/desktop/msi/customaction-table) ve özel eylem.

 50 türündeki özel eylemler, kaynak sütunun değeri olarak yürütülebilir dosyayı içeren özelliği ve hedef sütununda komut satırı bağımsız değişkenlerini belirtir.

### <a name="customaction-table-rows-to-run-devenvexe"></a>devenv.exe çalıştırılacak CustomAction tablosu satırları

|Eylem|Tür|Kaynak|Hedef|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Yükleme sırasında yürütülmek üzere zamanlamak için, özel eylemler InstallExecuteSequence tablosuna yazılmalıdır. Bu sürümü sistemde yüklü değilse özel eylemin çalıştırılmasını engellemek için koşul sütununun her satırında karşılık gelen özelliğini kullanın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

> [!NOTE]
> Koşullarda kullanıldığında null değerli özellikler olarak değerlendirilir `False` .

 her bir özel eylem için dizi sütununun değeri, Windows Installer paketinizin diğer sıra değerlerine bağlıdır. Sıra değerleri, *devenv.exe* özel eylemlerin, InstallFinalize standart eyleminden hemen önce mümkün olduğunca yakın şekilde çalışmasını sağlamalıdır.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>devenv.exe özel eylemleri zamanlamak için InstallExecuteSequence tablosu

|Eylem|Koşul|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile vspackages 'i yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
