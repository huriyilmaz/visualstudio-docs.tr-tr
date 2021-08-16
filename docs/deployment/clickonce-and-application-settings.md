---
title: ClickOnce ve Uygulama Ayarlar | Microsoft Docs
description: Uygulama ayarları dosyalarının bir ClickOnce nasıl ClickOnce kullanıcı bir sonraki sürüme yükseltilirken ayarları nasıl geçir olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6449a74a8649fa97ac4ff55cf57ea855892ba50baa9debacd064a39ffb70059d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404016"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce ve uygulama ayarları
Windows Forms için uygulama ayarları, istemcide özel uygulama ve kullanıcı tercihleri oluşturmanızı, depolamanızı ve korumanızı kolaylaştırır. Aşağıdaki belgede, uygulama ayarları dosyalarının bir ClickOnce uygulamasında nasıl ClickOnce kullanıcı bir sonraki sürüme yükseltilirken ayarları nasıl geçirt olduğu açıkmektedir.

 Aşağıdaki bilgiler yalnızca varsayılan uygulama ayarları sağlayıcısı olan sınıfı için <xref:System.Configuration.LocalFileSettingsProvider> geçerlidir. Özel bir sağlayıcı sağlarsanız bu sağlayıcı, verilerini nasıl depolasa da ayarlarını sürümler arasında nasıl yükselteceklerini belirler. Uygulama ayarları sağlayıcıları hakkında daha fazla bilgi için bkz. [Uygulama ayarları mimarisi.](/dotnet/framework/winforms/advanced/application-settings-architecture)

## <a name="application-settings-files"></a>Uygulama ayarları dosyaları
 Uygulama ayarları iki dosya kullanır: *\<app>.exe.config* *veuser.config*, *burada uygulama,* Windows Forms Windows adıdır. *user.config,* uygulama kullanıcı kapsamlı ayarları ilk kez depolayana kadar istemcide oluşturulur. *\<app>.exe.config,* buna karşılık, ayarlar için varsayılan değerleri tanımlarsanız dağıtımdan önce mevcut olacaktır. Visual Studio, Yayımla komutunu kullanarak bu dosyayı otomatik **olarak içerecektir.** ClickOnce veyaMageUI.exekullanarak *Mage.exe,* *uygulama* bildiriminizi doldurmak için bu dosyanın uygulamanın diğer dosyalarına dahil olduğundan emin olun.

 ClickOnce kullanılarak dağıtılan Windows Forms uygulamasında bir *\<app> uygulamanın.exe.config* dosyası uygulama dizininde depolanırken, *user.config* dosyası kullanıcının Documents ve **Ayarlar klasöründe** depolanır. Bir ClickOnce uygulamada *\<app>.exe.config* ClickOnce uygulama önbelleğinin içindeki uygulama dizininde,user.configise  bu uygulamanın ClickOnce veri dizininde bulunur.

 Uygulamanızı nasıl dağıtacak olur olmaz, uygulama ayarları.exe.config *\<app> 'ye* güvenli okuma erişimi ve uygulama ayarlarına güvenli okuma/yazma *erişimiuser.config.*

 Bir ClickOnce uygulamanın uygulama ayarları tarafından kullanılan yapılandırma dosyalarının boyutu, uygulama önbelleğinin boyutuyla ClickOnce kısıtlanmış olur. Daha fazla bilgi için [bkz. ClickOnce önbelleğine genel bakış.](../deployment/clickonce-cache-overview.md)

## <a name="version-upgrades"></a>Sürüm yükseltmeleri
 Bir ClickOnce uygulamasının her sürümü diğer tüm sürümlerden yalıtılmış olduğu gibi, ClickOnce bir uygulamanın uygulama ayarları da diğer sürümlerin ayarlarından yalıtılmıştır. Kullanıcınız, uygulama ayarlarınızın sonraki bir sürümüne yükseltdiğinde, uygulama ayarları en son (en yüksek numaralı) sürümün ayarlarını güncelleştirilmiş sürümle sağlanan ayarlarla karşılar ve ayarları yeni bir ayar dosyaları kümesiyle birler.

 Aşağıdaki tabloda, uygulama ayarlarının hangi ayarları kopyalayıp kopyalaymayacaklarını nasıl karara varma adımları açıkmektedir.

|Değişiklik Türü|Yükseltme Eylemi|
|--------------------|--------------------|
|*\<app>.exe.config'a eklenen ayar*|Yeni ayar geçerli sürümün veri *\<app>*.exe.config|
|Ayar, *\<app>.exe.config'den kaldırıldı*|Eski ayar geçerli sürümün.exe.config *\<app>*|
|Ayarın varsayılan değeri değiştirildi; yerel ayar yine de varsayılan olarak özgün *user.config*|Ayar, geçerli sürümünuser.config *değeri* olarak yeni varsayılan değerle birleştirilir|
|Ayarın varsayılan değeri değiştirildi; ayarı,user.config'de varsayılan *olmayan olarakuser.config*|Ayar, geçerli sürümünuser.config *varsayılan* olmayan değer korunarak birleştirilir|

Kendi uygulama ayarları sarmalayıcı sınıfınızı oluşturduysanız ve güncelleştirme mantığını özelleştirmek isterseniz yöntemini geçersiz <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> kılabilirsiniz.

## <a name="clickonce-and-roaming-settings"></a>ClickOnce ve dolaşım ayarları
 ClickOnce, dolaşım ayarlarıyla birlikte çalışmaz ve bu da ayarlar dosyanız sizi bir ağ üzerinde makineler arasında izlemenizi sağlar. Dolaşım ayarlarına ihtiyacınız varsa, ayarları ağ üzerinden depolayarak bir uygulama ayarları sağlayıcısı uygulamanız veya ayarları uzak bir bilgisayarda depolamak için kendi özel ayarlar sınıflarınızı geliştirmeniz gerekir. Ayar sağlayıcıları hakkında daha fazla bilgi için [bkz. Uygulama ayarları mimarisi.](/dotnet/framework/winforms/advanced/application-settings-architecture)

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Uygulama ayarlarına genel bakış](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md)
- [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)