---
title: '&lt;entryPoint &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
description: EntryPoint öğesi, bu ClickOnce uygulaması bir istemci bilgisayarda çalıştırıldığında yürütülmesi gereken derlemeyi tanımlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5c35d94001ae1e883e2bd76650f248d7e0364d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893899"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint &gt; öğesi (ClickOnce uygulaması)
Bu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bir istemci bilgisayarda çalıştırıldığında yürütülmesi gereken derlemeyi tanımlar.

## <a name="syntax"></a>Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `entryPoint`Öğesi gereklidir ve `urn:schemas-microsoft-com:asm.v2` ad alanında bulunur. `entryPoint`Uygulama bildiriminde yalnızca bir öğe tanımlanmış olabilir.

 `entryPoint`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|İsteğe bağlı. Bu değer .NET Framework tarafından kullanılmaz.|

 `entryPoint` Aşağıdaki öğelere sahiptir.

## <a name="assemblyidentity"></a>AssemblyIdentity
 Gereklidir. `assemblyIdentity`Ve özniteliklerinin rolü [ \<assemblyIdentity> öğesinde](../deployment/assemblyidentity-element-clickonce-application.md)tanımlanmıştır.

 `processorArchitecture`Bu öğenin özniteliği ve `processorArchitecture` `assemblyIdentity` uygulama bildiriminde bir yerde tanımlanan özniteliğin eşleşmesi gerekir.

## <a name="commandline"></a>Komut satırı
 Gereklidir. Öğenin bir alt `entryPoint` öğesi olmalıdır. Alt öğesi yoktur ve aşağıdaki özniteliklere sahiptir.

| Öznitelik | Açıklama |
|--------------| - |
| `file` | Gereklidir. Uygulama için başlangıç derlemesine yerel bir başvuru [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu değer eğik çizgi (/) veya ters eğik çizgi ( \\ ) yol ayırıcıları içeremez. |
| `parameters` | Gereklidir. Giriş noktasıyla gerçekleştirilecek eylemi açıklar. Geçerli tek değer `run` ; boş bir dize sağlanırsa `run` kabul edilir. |

## <a name="customhostrequired"></a>customHostRequired
 İsteğe bağlı. Dahil ise, bu dağıtımın özel bir ana bilgisayar içinde dağıtılacak bir bileşen içerdiğini ve tek başına bir uygulama olmadığını belirtir.

 Bu öğe mevcutsa, `assemblyIdentity` ve `commandLine` öğeleri de bulunmamalıdır. Bunlar, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yükleme sırasında bir doğrulama hatası oluşturacak.

 Bu öğenin hiç özniteliği yok ve alt öğesi yok.

## <a name="customux"></a>customUX
 İsteğe bağlı. Uygulamanın özel bir yükleyici tarafından yüklenip korunur olduğunu ve bir Başlat menüsü girdisi, kısayol veya Program Ekle veya Kaldır girdisi oluşturmadığından emin olarak belirtir.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 CustomUX öğesini içeren bir uygulamanın, <xref:System.Deployment.Application.InPlaceHostingManager> yükleme işlemlerini gerçekleştirmek için sınıfını kullanan özel bir yükleyici sağlaması gerekir. Bu öğeye sahip bir uygulama, bildirimine veya önkoşul önyükleyici setup.exe ' ye çift tıklayarak yüklenemez. Özel yükleyici, Başlat menüsü girdileri, kısayolları ve Program Ekle veya Kaldır girdilerini oluşturabilir. Özel yükleyici Program Ekle veya Kaldır girdisi içermiyorsa, özelliği tarafından sağlanmış abonelik tanımlayıcısını depolamalıdır <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> ve kullanıcıyı daha sonra metodunu çağırarak uygulamayı kaldırmasını sağlar <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> . Daha fazla bilgi için bkz. [Izlenecek yol: ClickOnce uygulaması Için özel bir yükleyici oluşturma](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Açıklamalar
 Bu öğe, uygulamanın derlemesini ve giriş noktasını tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 `commandLine`Çalışma zamanında uygulamanıza parametreleri geçirmek için kullanamazsınız. Uygulamanın bir dağıtım için sorgu dizesi parametrelerine erişebilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] <xref:System.AppDomain> . Daha fazla bilgi için bkz. [nasıl yapılır: sorgu dizesi bilgilerini bir çevrimiçi ClickOnce uygulamasında alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `entryPoint` bir uygulama için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu kod örneği, [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
