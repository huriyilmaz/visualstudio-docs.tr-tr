---
title: ClickOnce ve uygulama Ayarlar | Microsoft Docs
description: uygulama ayarları dosyalarının bir ClickOnce uygulamasında nasıl çalıştığını ve kullanıcı bir sonraki sürüme yükseltirken ayarları ClickOnce nasıl geçirdiğini öğrenin.
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
ms.openlocfilehash: 2e321f905e4bad8139705b8f9bcb6139c5d10a9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051657"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce ve uygulama ayarları
Windows Forms için uygulama ayarları, istemci üzerinde özel uygulama ve kullanıcı tercihleri oluşturmayı, depolamayı ve bakımını yapmayı kolaylaştırır. aşağıdaki belge, uygulama ayarları dosyalarının ClickOnce bir uygulamada nasıl çalıştığını ve kullanıcı bir sonraki sürüme yükseltildiğinde ClickOnce ayarları nasıl geçirdiğini açıklar.

 Aşağıdaki bilgiler yalnızca varsayılan uygulama ayarları sağlayıcısı, sınıfı için geçerlidir <xref:System.Configuration.LocalFileSettingsProvider> . Özel bir sağlayıcı sağlarsanız, bu sağlayıcı, verileri nasıl depoladığını ve sürümler arasında ayarlarını nasıl yükseltleyeceğini tespit eder. Uygulama ayarları sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Uygulama ayarları dosyaları
 uygulama ayarları iki dosya tüketir: *\<app>.exe.config* ve *user.config*, burada *uygulama* Windows Forms uygulamanızın adıdır. *user.config* , uygulamanız kullanıcı kapsamlı ayarları depolaışında istemci üzerinde oluşturulur. Ayarlar için varsayılan değerler tanımlarsanız, buna karşılık olarak *\<app>.exe.config*, dağıtımdan önce mevcut olacaktır. Visual Studio, **yayımla** komutunu kullandığınızda bu dosyayı otomatik olarak içerecektir. ClickOnce uygulamanızı *Mage.exe* veya *MageUI.exe* kullanarak oluşturursanız, uygulama bildiriminizi doldurduğunuzda bu dosyanın uygulamanızın diğer dosyalarına eklendiğinden emin olmanız gerekir.

 ClickOnce kullanılarak dağıtılan Windows Forms bir uygulamada, bir uygulamanın *\<app>.exe.config* dosyası uygulama dizininde depolanır, ancak *user.config* dosyası kullanıcının **belgelerine ve Ayarlar** klasörüne depolanır. ClickOnce bir uygulamada, *\<app>.exe.config* ClickOnce uygulama önbelleğinin içindeki uygulama dizininde bulunur ve *user.config* bu uygulama için ClickOnce veri dizininde bulunur.

 Uygulamanızı nasıl dağıtabileceğinizi göz önüne alarak, uygulama ayarları *\<app>.exe.config* için güvenli okuma erişimi ve *user.config* güvenli okuma/yazma erişimi sağlar.

 ClickOnce bir uygulamada, uygulama ayarları tarafından kullanılan yapılandırma dosyalarının boyutu, ClickOnce önbelleğinin boyutuyla sınırlıdır. daha fazla bilgi için bkz. [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Sürüm yükseltmeleri
 bir ClickOnce uygulamasının her bir sürümü diğer tüm sürümlerden yalıtılmış olduğu için, bir ClickOnce uygulamasının uygulama ayarları da diğer sürümlerin ayarlarından yalıtılmıştır. Kullanıcı uygulamanızın daha sonraki bir sürümüne yükselttiğinde, uygulama ayarları en son (en yüksek sayılı) sürüm ayarlarını, güncelleştirilmiş sürümle sağlanan ayarlarla karşılaştırır ve ayarları yeni bir ayar dosyaları kümesiyle birleştirir.

 Aşağıdaki tabloda, uygulama ayarlarının hangi ayarların kopyalanacağını nasıl karar verdiği açıklanmaktadır.

|Değişiklik türü|Yükseltme eylemi|
|--------------------|--------------------|
|*\<app>.exe.config* ayarı eklendi|Yeni ayar, geçerli sürümün *\<app>.exe.config* birleştirilir|
|*\<app>.exe.config* kaldırılan ayar|Eski ayar geçerli sürümden kaldırılır *\<app>.exe.config*|
|Ayarın varsayılan değiştirildi; Yerel ayar hala *user.config* özgün varsayılana ayarlanmış|Bu ayar, geçerli sürümün *user.config* , yeni varsayılan değer olarak ile birleştirilir|
|Ayarın varsayılan değiştirildi; *user.config* ' de varsayılan olmayan ayar ayarlandı|Ayar, geçerli sürüm *user.config* ile birleştirilir ve varsayılan olmayan değer korunur|

Kendi uygulama ayarları sarmalayıcı sınıfınızı oluşturduysanız ve güncelleştirme mantığını özelleştirmek istiyorsanız, yöntemini geçersiz kılabilirsiniz <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> .

## <a name="clickonce-and-roaming-settings"></a>ClickOnce ve dolaşım ayarları
 ClickOnce, ayarlar dosyanızın bir ağdaki makinelerde sizi izlemesini sağlayan dolaşım ayarlarıyla çalışmaz. Dolaşım ayarlarına ihtiyacınız varsa, ayarları ağ üzerinden depolayan bir uygulama ayarları sağlayıcısı uygulamanız veya ayarları uzak bir bilgisayarda depolamak için kendi özel ayar sınıflarınızı geliştirmeniz gerekir. Ayarlar sağlayıcıları hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Uygulama ayarlarına genel bakış](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md)
- [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)