---
title: İçinde kullanılan değiştirme dizeleri. Pkgdef ve. Pkgundef dosyaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160539"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>.Pkgdef ve .Pkgundef Dosyalarında Kullanılan Değiştirme Dizeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio yalıtılmış Kabuk uygulamanız için tanımladığınız. pkgdef ve. pkgundef dosyalarında aşağıda listelenen değiştirme dizelerini kullanabilirsiniz.  
  
## <a name="substitution-strings"></a>Değiştirme dizeleri  
  
|Dize|Açıklama|  
|------------|-----------------|  
|$=*RegistryEntry*$|*RegistryEntry* girişinin değeri. Kayıt defteri giriş dizesi bir ters eğik çizgi ( \\ ) ile sonlanıyorsa, kayıt defteri alt anahtarının varsayılan değeri kullanılır. Örneğin, $ = HKEY_CURRENT_USER \Environment\TEMP $ değiştirme dizesi, geçerli kullanıcının geçici klasörüne genişletilir.|  
|$AppName $|AppEnv.dll giriş noktalarına geçirilen uygulamanın tam adı. Nitelikli ad, uygulama adı, alt çizgi ve uygulama Otomasyon nesnesinin sınıf tanımlayıcısından (CLSID) oluşur. Bu, Project. pkgdef dosyasındaki ThisVersionDTECLSID ayarının değeri olarak da kaydedilir.|  
|$AppDataLocalFolder|Bu uygulama için% LOCALAPPDATA% altındaki alt klasör.|  
|$BaseInstallDir $|Visual Studio 'Nun yüklendiği konumun tam yolu.|  
|$CommonFiles $|% CommonProgramFiles% ortam değişkeninin değeri.|  
|$MyDocuments $|Geçerli kullanıcının Belgelerim klasörünün tam yolu.|  
|$PackageFolder $|Uygulamanın paket derleme dosyalarını içeren dizinin tam yolu.|  
|$ProgramFiles $|% ProgramFiles% ortam değişkeninin değeri.|  
|$RootFolder $|Uygulamanın kök dizininin tam yolu.|  
|$RootKey $|Uygulamanın kök kayıt defteri anahtarı. Kök, varsayılan olarak HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *ProjectName* \\ *versionNumber* (uygulama çalışırken _Config bu anahtara eklenir). *SolutionName*. pkgdef dosyasındaki RegistryRoot değeri tarafından ayarlanır.<br /><br /> $RootKey $ dizesi, uygulama alt anahtarı altında bir kayıt defteri değeri almak için kullanılabilir. Örneğin, "$ = $RootKey $ \Appıcon $" dizesi, uygulama kök alt anahtarı altında AppIcon girişinin değerini döndürür.<br /><br /> Ayrıştırıcı,. pkgdef dosyasını sırayla işler ve yalnızca giriş önceden tanımlanmışsa uygulama alt anahtarı altında bir kayıt defteri girişine erişebilir|  
|$ShellFolder $|Visual Studio 'Nun yüklendiği konumun tam yolu.|  
|$System $|Windows\System32 klasörü.|  
|$WINDIR $|Windows klasörü.|  
  
 Ayrıştırıcı değiştirme dizesini tanımıyor veya bir kayıt defteri girdisinin veya bir ortam değişkeninin değerini belirleyemezse, dizenin o bölümünde değiştirme yapmaz.
