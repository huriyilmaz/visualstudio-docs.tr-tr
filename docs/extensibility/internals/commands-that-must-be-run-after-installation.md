---
title: Yükleme Sonrasında Çalıştıracak Komutlar | Microsoft Docs
description: Visual Studio'da bir .msi dosyası aracılığıyla dağıtılan bir uzantı yüklemenizin bir parçası olarak çalıştırılacak komutlar hakkında Visual Studio.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050188"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yüklemeden sonra çalıştıracak komutlar
Uzantınızı bir.msi dosyası aracılığıyla dağıtırsanız, uzantılarınızı bulmanız için yüklemenizin bir parçası olarak **devenv /setup** Visual Studio gerekir.

> [!NOTE]
> Bu konudaki bilgiler, 2008 *vedevenv.exe* ile Visual Studio için geçerlidir. Uygulamanın sonraki sürümleriyle *devenv.exe* bulma hakkında daha fazla bilgi Visual Studio [bkz. Sistem gereksinimlerini algılama.](../../extensibility/internals/detecting-system-requirements.md)

## <a name="find-devenvexe"></a>Yeni devenv.exe
 Kayıt defteri değerlerini özellikler olarak *depolamakdevenv.exe* RegLocator tablosu ve AppSearch tablolarını kullanarak yükleyicilerin yazmış olduğu kayıt defteri değerlerinden her bir sürümün özelliklerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bulun. Daha fazla bilgi için [bkz. Sistem gereksinimlerini algılama.](../../extensibility/internals/detecting-system-requirements.md)

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator tablo satırları, devenv.exe sürümlerinin farklı sürümlerini Visual Studio

|İmza|Root|Anahtar|Ad|Tür|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>İlgili RegLocator tablo satırları için AppSearch tablo satırları

|Özellik|İmza|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Örneğin, Visual Studio kayıt defteri değerini **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** olarak *yazarC:\VS2008\Common7\IDE\devenv.exe,* yükleyicinin çalışması gereken yürütülebilir dosyanın tam yoludur.

> [!NOTE]
> RegLocator tablonun Tür sütunu 2 olduğundan, signature tablosunda ek sürüm bilgileri belirtmek gerekli değildir.

## <a name="run-devenvexe"></a>Çalıştırma devenv.exe
 AppSearch standart eylemi yükleyicide çalıştırıldıktan sonra, AppSearch tablodaki her özelliğin, uygulamanın ilgili sürümü için *devenv.exe* dosyasına işaret Visual Studio. Belirtilen kayıt defteri değerlerden herhangi biri yoksa — Visual Studio sürümü yüklenmemişse— belirtilen özellik null olarak ayarlanır.

 Windows Yükleyici, bir özelliğin özel eylem türü 50'ye göre bir yürütülebilir dosyayı çalıştırmayı destekler. Özel eylem, VSPackage'ın ile tümleştirimeden önce başarıyla yüklenmiş olduğundan emin olmak için betik içinde yürütme seçeneklerini `msidbCustomActionTypeInScript` `msidbCustomActionTypeCommit` (1024) ve (512) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] içermeli. Daha fazla bilgi için bkz. [CustomAction tablosu](/windows/desktop/msi/customaction-table) [ve Özel eylem betik içinde yürütme seçenekleri.](/windows/desktop/msi/custom-action-in-script-execution-options)

 50 türünde özel eylemler, Yürütülebilir dosyayı Içeren özelliği Source sütun değeri olarak ve Target sütunundaki komut satırı bağımsız değişkenlerini belirtir.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Veri çalıştırmak için CustomAction tablo devenv.exe

|Eylem|Tür|Kaynak|Hedef|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Özel eylemlerin yükleme sırasında yürütme için zamanlaması için InstallExecuteSequence tablosuna yazması gerekir. Özel eylemin sistemde yüklü olması durumunda çalıştırılamaması için Koşul sütunlarının her bir satırına karşılık gelen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özelliği kullanın.

> [!NOTE]
> Null değerli özellikler, koşullarda `False` kullanılırken olarak değerlendirilir.

 Her özel eylem için Sıra sütun değeri, yükleyici yükleyici paketinizin diğer Windows bağlıdır. Sıra değerleri, özel *eylemlerindevenv.exe* InstallFinalize standart eylemden hemen önce mümkün olduğunca yakın çalıştıracak şekilde olması gerekir.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Özel eylemleri zamanlaması için InstallExecuteSequence devenv.exe tablosu

|Eylem|Koşul|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Ayrıca bkz.
- [WINDOWS Yükleyicisi ile VSPackage'ları yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
