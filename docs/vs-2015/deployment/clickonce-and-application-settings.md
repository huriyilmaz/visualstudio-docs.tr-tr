---
title: ClickOnce ve uygulama ayarları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696684"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce ve Uygulama Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms için uygulama ayarları, istemci üzerinde özel uygulama ve Kullanıcı tercihleri oluşturmayı, depolamayı ve bakımını yapmayı kolaylaştırır. Aşağıdaki belge, uygulama ayarları dosyalarının bir ClickOnce uygulamasında nasıl çalıştığını ve Kullanıcı bir sonraki sürüme yükseltildiğinde ClickOnce 'ın ayarları nasıl geçirdiğini açıklar.  
  
 Aşağıdaki bilgiler yalnızca varsayılan uygulama ayarları sağlayıcısı, sınıfı için geçerlidir <xref:System.Configuration.LocalFileSettingsProvider> . Özel bir sağlayıcı sağlarsanız, bu sağlayıcı, verileri nasıl depoladığını ve sürümler arasında ayarlarını nasıl yükseltleyeceğini tespit eder. Uygulama ayarları sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Uygulama ayarları dosyaları  
 Uygulama ayarları iki dosya tüketir: *app.exe.config ve* user.config, burada *uygulama* Windows Forms uygulamanızın adıdır. user.config, uygulamanız kullanıcı kapsamlı ayarları depolaışında istemci üzerinde oluşturulur. ayarlar için varsayılan değerler tanımlarsanız, buna karşılık olarak *uygulama*.exe.config, dağıtımdan önce mevcut olacaktır. **Yayımla** komutunu kullandığınızda, Visual Studio bu dosyayı otomatik olarak içerecektir. ClickOnce uygulamanızı Mage.exe veya MageUI.exe kullanarak oluşturursanız, uygulama bildiriminizi doldurduğunuzda bu dosyanın uygulamanızın diğer dosyalarına eklendiğinden emin olmanız gerekir.  
  
 ClickOnce kullanılarak dağıtılan Windows Forms uygulamalarda *, uygulamanın uygulama.exe.config dosyası* uygulama dizininde depolanır, ancak user.config dosyası kullanıcının **Belgeler ve ayarlar** klasöründe depolanır. ClickOnce uygulamasında, *uygulama*.exe.config ClickOnce uygulama önbelleğinin içindeki uygulama dizininde bulunur ve bu uygulamanın ClickOnce veri dizininde bulunur user.config.  
  
 Uygulamanızı nasıl dağıtabileceğinizi ne olursa olsun *, uygulama ayarları, uygulama.exe.config güvenli* okuma erişimi ve user.config için güvenli okuma/yazma erişimi sağlar.  
  
 ClickOnce uygulamasında, uygulama ayarları tarafından kullanılan yapılandırma dosyalarının boyutu ClickOnce önbelleğinin boyutuyla sınırlıdır. Daha fazla bilgi için bkz. [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Sürüm yükseltmeleri  
 ClickOnce uygulamasının her sürümü diğer tüm sürümlerden yalıtılmış olduğu gibi, bir ClickOnce uygulaması için uygulama ayarları da diğer sürümlerin ayarlarından yalıtılmıştır. Kullanıcı uygulamanızın daha sonraki bir sürümüne yükselttiğinde, uygulama ayarları en son (en yüksek sayılı) sürüm ayarlarını, güncelleştirilmiş sürümle sağlanan ayarlarla karşılaştırır ve ayarları yeni bir ayar dosyaları kümesiyle birleştirir.  
  
 Aşağıdaki tabloda, uygulama ayarlarının hangi ayarların kopyalanacağını nasıl karar verdiği açıklanmaktadır.  
  
|Değişiklik türü|Yükseltme eylemi|  
|--------------------|--------------------|  
|*Uygulamaya* eklenen ayar.exe.config|Yeni ayar, geçerli sürümün *uygulamasıyla* birleştirilir.exe.config|  
|*Uygulama*.exe.config ilke kaldırıldı|Eski ayar, geçerli *sürümün uygulamasından kaldırılır.exe.config*|  
|Ayarın varsayılan değiştirildi; Yerel ayar hala user.config özgün varsayılana ayarlanmış|Bu ayar, geçerli sürümün user.config, yeni varsayılan değer olarak ile birleştirilir|  
|Ayarın varsayılan değiştirildi; user.config ' de varsayılan olmayan ayar ayarlandı|Ayar, geçerli sürüm user.config ile birleştirilir ve varsayılan olmayan değer korunur|  
  
 Kendi uygulama ayarları sarmalayıcı sınıfınızı oluşturduysanız ve güncelleştirme mantığını özelleştirmek istiyorsanız, yöntemini geçersiz kılabilirsiniz <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> .  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce ve dolaşım ayarları  
 ClickOnce, ayarlar dosyanızın bir ağdaki makineler arasında sizi izlemesini sağlayan dolaşım ayarları ile çalışmaz. Dolaşım ayarlarına ihtiyacınız varsa, ayarları ağ üzerinden depolayan bir uygulama ayarları sağlayıcısı uygulamanız veya ayarları uzak bir bilgisayarda depolamak için kendi özel ayar sınıflarınızı geliştirmeniz gerekir. Ayarlar sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Uygulama ayarlarına genel bakış](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md)   
 [ClickOnce Uygulamalarında Yerel ve Uzak Veri Erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
