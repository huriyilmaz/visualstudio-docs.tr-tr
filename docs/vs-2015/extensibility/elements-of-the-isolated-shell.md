---
title: Yalıtılmış kabuğun öğeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204612"
---
# <a name="elements-of-the-isolated-shell"></a>Yalıtılmış Kabuğun Öğeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalıtılmış Kabuk uygulamanızın kayıt defteri ayarlarını, çalışma zamanı ayarlarını ve uygulama giriş noktasını ve. vsct,. pkgdef ve. pkgundef dosyalarını değiştirebilirsiniz.  
  
## <a name="registry-settings"></a>Kayıt Defteri Ayarları  
 . Pkgdef ve. pkgundef dosyaları, yalıtılmış Kabuk uygulaması için kayıt defteri ayarlarını değiştirir. Uygulama çalıştırıldığında, kayıt defteri ayarları aşağıdaki sırada tanımlanır:  
  
 Uygulama çalıştırıldığında, kayıt defteri ayarları aşağıdaki sırada tanımlanır:  
  
1. Uygulama için kayıt defteri anahtarı oluşturulur.  
  
2. Kayıt defteri, belirtilen anahtarları ve girişleri tanımlayarak uygulamanın. pkgdef dosyasından güncelleştirilir.  
  
3. Uygulamanızın parçası olan her paket için kayıt defteri Bu paketin. pkgdef dosyasından güncelleştirilir. Her paket, paket için $RootKey $ \Packages \\ {*VsPackageGuid*} anahtarıyla uygulamanın. pkgdef dosyasında tanımlanır.  
  
4. Kayıt defteri, *Visual STUDIO SDK yükleme yolu*\Common7\IDE\ShellExtensions\Platform dizinindeki AppEnvConfig. pkgdef ve BaseConfig. pkgdef öğesinden güncelleştirilir. Bu dosyalar, Visual Studio 'nun bir parçasıdır ve Visual Studio Kabuğu (yalıtılmış mod) yeniden dağıtılabilir paketi 'nin bir parçasıdır.  
  
5. Kayıt defteri, belirtilen anahtarlar ve girdileri kaldırarak uygulamanın. pkgundef dosyasından güncelleştirilir.  
  
## <a name="run-time-settings"></a>Çalışma zamanı ayarları  
 Kullanıcı yalıtılmış kabuk uygulamasını başlattığında, Visual Studio Kabuğu 'nun başlangıç giriş noktasını çağırır. Uygulama ayarları, uygulamanız başlatıldığında aşağıdaki gibi tanımlanır:  
  
1. Visual Studio Kabuğu, uygulama kayıt defterini belirli anahtarlar için denetler. Başlangıç giriş noktasına yapılan çağrıda bir anahtarın ayarı belirtilmişse, bu değer kayıt defterindeki değeri geçersiz kılar.  
  
2. Kayıt defteri veya giriş noktası parametresi bir ayarın değerini belirtiyorsa, ayar için varsayılan değer kullanılır.  
  
   Bir kullanıcı uygulamanızı komut satırından başlattığında, tüm komut satırı anahtarları Visual Studio Shell 'e geçirilir ve bu, devenv tarafından aynı şekilde davranır. Devenv anahtarları hakkında daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md) ve [VSPackage geliştirme Için Devenv komut satırı anahtarları](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Bir paketin komut satırı anahtarlarına nasıl kaydolduktan ilişkin daha fazla bilgi için bkz. [komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Başlangıç giriş noktası  
 Appenvstub.dll dosyası yalıtılmış kabuğa erişmek için giriş noktaları içerir. Uygulama başlatıldığında Appenvstub.dll başlangıç giriş noktasını çağırır.  
  
 Başlangıç giriş noktasına geçirilen son parametrenin değerini değiştirerek uygulamanın davranışını değiştirebilirsiniz. Daha fazla bilgi için bkz. [yalıtılmış Kabuk giriş noktası parametreleri (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>İçin. Vsct dosyası  
 . Vsct dosyası, uygulamada hangi standart Visual Studio Kullanıcı arabirimi öğelerinin kullanılabilir olduğunu belirtmenizi sağlar. Daha fazla bilgi için bkz [.. Vsct dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>İçin. Pkgundef dosyası  
 Uygulama, Visual Studio 'nun zaten yüklü olduğu bir bilgisayara yüklendiğinde, uygulama için Visual Studio kayıt defteri girdilerinin bir kopyası yapılır. Varsayılan olarak, uygulama bilgisayarda zaten yüklü olan VSPackages 'yi kullanır. . Pkgundef dosyası, Visual Studio kabuğu veya uzantılarının belirli öğelerini uygulamadan kaldırmak için kayıt defteri girdilerini dışlamanızı sağlar. Daha fazla bilgi için bkz [.. Pkgundef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 . Pkgundef dosyası, Visual Studio kabuğu veya uzantılarının belirli öğelerini uygulamadan kaldırmak için kayıt defteri girdilerini dışlamanızı sağlar. Daha fazla bilgi için bkz [.. Pkgundef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Dışarıda bırakabilmeniz gereken paket GUID 'Leri kümesi, [Visual Studio özelliklerinin paket GUID](../extensibility/package-guids-of-visual-studio-features.md)'lerinde listelenmiştir.  
  
## <a name="the-pkgdef-file"></a>İçin. Pkgdef dosyası  
 . Pkgdef dosyası, uygulama yüklendiğinde ayarlanan uygulama için kayıt defteri girişleri tanımlamanızı sağlar. . Pkgdef dosyasının açıklaması ve Visual Studio Kabuğu 'nun kullandığı kayıt defteri girdilerinin bir listesi için bkz [.. Pkgdef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Değiştirme dizeleri  
 . Pkgdef ve. pkgundef dosyalarında kullanılan değiştirme dizeleri, [' de kullanılan değiştirme dizelerinde listelenmiştir. Pkgdef ve. Pkgundef dosyaları](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Diğer ayarlar  
 Yalıtılmış Kabuk uygulamanız Microsoft.VisualStudio.GraphModel.dll bağımlıysa, yalıtılmış Kabuk uygulamanızın. config dosyasına aşağıdaki bağlama yeniden yönlendirmesini eklemeniz gerekir:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
