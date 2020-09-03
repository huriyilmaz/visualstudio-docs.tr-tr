---
title: VSPackage geliştirmesi için Devenv komut satırı anahtarları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185273"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage Geliştirme için Devenv Komut Satırı Anahtarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] geliştiricilerin, Visual Studio tümleşik geliştirme ortamı 'nı (IDE) başlatan dosya devenv.exe yürütürken görevleri komut satırından otomatikleştirmesini sağlar.  
  
 Görevler şunları içerir:  
  
- Uygulamaları, IDE dışından önceden tasarlanmış yapılandırmalara dağıtma.  
  
- Önceden ayarlanmış yapı ayarlarını veya hata ayıklama yapılandırmasını kullanarak projeleri otomatik olarak derleme.  
  
- IDE 'nin dışındaki belirli yapılandırmalarda IDE 'yi yükleme. Ayrıca, başlatma sonrasında IDE 'yi özelleştirebilirsiniz.  
  
## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belgeler, Kullanıcı düzeyi Devenv komut satırı anahtarlarını açıklar. Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md). Devenv, VSPackage geliştirme, dağıtım ve hata ayıklama ile yararlı olan ek komut satırı anahtarlarını da destekler.  
  
|Komut satırı anahtarı|Açıklama|  
|--------------------------|-----------------|  
|/safemode|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Yalnızca varsayılan IDE ve Hizmetleri yükleyerek güvenli modda başlatılır. /Safemode anahtarı, başlatıldığında tüm üçüncü taraf VSPackages 'nin yüklenmesini engeller [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve böylece kararlı yürütmeyi sağlar.<br /><br /> Bu anahtar bağımsız değişken almaz.|  
|/resetskippkgs|Sorunlu VSPackages yüklemeden kaçınmak isteyen kullanıcılar tarafından eklenmiş tüm yükleme seçeneklerini temizler ve sonra başlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bir Skipyükleme etiketinin varlığı, VSPackage yüklemesini devre dışı bırakır. Etiketi temizlemek, VSPackage yüklemesini yeniden etkinleştirilir.<br /><br /> Bu anahtar bağımsız değişken almaz.|  
|/rootsuffix|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Alternatif bir konum kullanılarak başlar. Aşağıdaki komut, yükleyici tarafından oluşturulan kısayol tarafından çalıştırılır [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] :<br /><br /> Devenv/RootSuffix exp<br /><br /> Bu durumda, exp belirli bir sonek içeren bir konum tanımlar, örneğin 10,0 yerine 10.0 exp. Deneysel örnek, bir VSPackage 'ın kod yazmak için kullandığınız örneğinden ayrı olarak hata ayıklamanıza olanak tanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .<br /><br /> Bu anahtar, VSRegEx.exe kullanarak oluşturduğunuz bir konumu tanımlayan herhangi bir dizeyi alabilir. Daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).|  
|/giriş|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Giriş ekranını her zamanki gibi gösterir ve ana IDE 'yi göstermeden önce bir ileti kutusu görüntüler. İleti kutusu, örneğin bir VSPackage ürün simgesini denetlemek için giriş ekranını denetlemenize olanak tanır.<br /><br /> Bu anahtar bağımsız değişken almaz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md)   
 [Devenv Komut Satırı Anahtarları](../ide/reference/devenv-command-line-switches.md)
