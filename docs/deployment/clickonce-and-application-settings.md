---
title: ClickOnce ve uygulama ayarları | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a72b5bc3f3645d9af1008f2c178ab285e8b45449
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184139"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce ve uygulama ayarları
Windows Forms için uygulama ayarları, istemci üzerinde özel uygulama ve Kullanıcı tercihleri oluşturmayı, depolamayı ve bakımını yapmayı kolaylaştırır. Aşağıdaki belge, uygulama ayarları dosyalarının bir ClickOnce uygulamasında nasıl çalıştığını ve Kullanıcı bir sonraki sürüme yükseltildiğinde ClickOnce 'ın ayarları nasıl geçirdiğini açıklar.

 Aşağıdaki bilgiler yalnızca varsayılan uygulama ayarları sağlayıcısı, sınıfı için geçerlidir <xref:System.Configuration.LocalFileSettingsProvider> . Özel bir sağlayıcı sağlarsanız, bu sağlayıcı, verileri nasıl depoladığını ve sürümler arasında ayarlarını nasıl yükseltleyeceğini tespit eder. Uygulama ayarları sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Uygulama ayarları dosyaları
 Uygulama ayarları iki dosya tüketir: * \<app> . exe. config* ve *User. config*, burada *uygulama* Windows Forms uygulamanızın adıdır. *User. config* , uygulamanız kullanıcı kapsamlı ayarları depoladığında istemci üzerinde oluşturulur. * \<app> . exe. config*, aksine, ayarlar için varsayılan değerler tanımlarsanız dağıtımdan önce mevcut olacaktır. **Yayımla** komutunu kullandığınızda, Visual Studio bu dosyayı otomatik olarak içerecektir. ClickOnce uygulamanızı *Mage. exe* veya *MageUI. exe*kullanarak oluşturursanız, uygulama bildiriminizi doldurduğunuzda bu dosyanın uygulamanızın diğer dosyalarına eklendiğinden emin olmanız gerekir.

 ClickOnce kullanılarak dağıtılan bir Windows Forms uygulamasında, bir uygulamanın * \<app> . exe. config* dosyası uygulama dizininde depolanır, ancak *User. config* dosyası kullanıcının **Documents and Settings** klasöründe depolanır. ClickOnce uygulamasında, * \<app> . exe. config* ClickOnce uygulama önbelleğinin içindeki uygulama dizininde bulunur ve *User. config* bu uygulamanın ClickOnce veri dizininde bulunur.

 Uygulamanızı nasıl dağıtabileceğinizi ne olursa olsun, uygulama ayarları, * \<app> . exe. config*dosyasına güvenli okuma erişiminin yanı sıra *User. config*dosyasına güvenli okuma/yazma erişimi sağlar.

 ClickOnce uygulamasında, uygulama ayarları tarafından kullanılan yapılandırma dosyalarının boyutu ClickOnce önbelleğinin boyutuyla sınırlıdır. Daha fazla bilgi için bkz. [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Sürüm yükseltmeleri
 ClickOnce uygulamasının her sürümü diğer tüm sürümlerden yalıtılmış olduğu gibi, bir ClickOnce uygulaması için uygulama ayarları da diğer sürümlerin ayarlarından yalıtılmıştır. Kullanıcı uygulamanızın daha sonraki bir sürümüne yükselttiğinde, uygulama ayarları en son (en yüksek sayılı) sürüm ayarlarını, güncelleştirilmiş sürümle sağlanan ayarlarla karşılaştırır ve ayarları yeni bir ayar dosyaları kümesiyle birleştirir.

 Aşağıdaki tabloda, uygulama ayarlarının hangi ayarların kopyalanacağını nasıl karar verdiği açıklanmaktadır.

|Değişiklik türü|Yükseltme eylemi|
|--------------------|--------------------|
|* \<app> . Exe. config* dosyasına eklenen ayar|Yeni ayar, geçerli sürümün * \<app> . exe. config dosyasında* birleştirilir|
|* \<app> . Exe. config* öğesinden kaldırılan ayar|Eski ayar geçerli sürümden * \<app> . exe. config* öğesinden kaldırılır|
|Ayarın varsayılan değiştirildi; Yerel ayar, *User. config* içinde hala özgün varsayılana ayarlanmış|Ayar, geçerli sürümün *User. config dosyasında* yeni varsayılan değer olarak birleştirilir|
|Ayarın varsayılan değiştirildi; *User. config* dosyasında varsayılan olmayan ayar ayarlandı|Ayar, geçerli sürümün *User. config dosyasında* , varsayılan olmayan değerle birleştirilir|

Kendi uygulama ayarları sarmalayıcı sınıfınızı oluşturduysanız ve güncelleştirme mantığını özelleştirmek istiyorsanız, yöntemini geçersiz kılabilirsiniz <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> .

## <a name="clickonce-and-roaming-settings"></a>ClickOnce ve dolaşım ayarları
 ClickOnce, ayarlar dosyanızın bir ağdaki makineler arasında sizi izlemesini sağlayan dolaşım ayarları ile çalışmaz. Dolaşım ayarlarına ihtiyacınız varsa, ayarları ağ üzerinden depolayan bir uygulama ayarları sağlayıcısı uygulamanız veya ayarları uzak bir bilgisayarda depolamak için kendi özel ayar sınıflarınızı geliştirmeniz gerekir. Ayarlar sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Uygulama ayarlarına genel bakış](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md)
- [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)