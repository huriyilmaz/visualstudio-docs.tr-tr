---
title: '&lt;Dağıtım &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 988ce0859ab24377395cc4077f9e6fa42e0487a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70887862"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Dağıtım &gt; öğesi (ClickOnce dağıtımı)
Güncelleştirmelerin dağıtımı için kullanılan öznitelikleri ve sistemde pozlandırmayı tanımlar.

## <a name="syntax"></a>Syntax

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `deployment`Öğesi gereklidir ve `urn:schemas-microsoft-com:asm.v2` ad alanında bulunur. Öğesi aşağıdaki özniteliklere sahiptir.

| Öznitelik | Açıklama |
|--------------------------| - |
| `install` | Gereklidir. Bu uygulamanın Windows **Başlat** menüsünde ve Denetim Masası **Program Ekle veya Kaldır** uygulamasında bir varlığı tanımlayıp tanımlamadığını belirtir. Geçerli değerler `true` ve ' dir `false` . `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Her zaman bu uygulamanın en son sürümünü ağdan çalıştırır ve `subscription` öğesini tanımaz. |
| `minimumRequiredVersion` | İsteğe bağlı. Bu uygulamanın istemcide çalışabilecek en düşük sürümünü belirtir. Uygulamanın sürüm numarası dağıtım bildiriminde sağlanan sürüm numarasından azsa, uygulama çalışmaz. Sürüm numaraları biçiminde belirtilmelidir `N.N.N.N` , burada `N` işaretsiz bir tamsayıdır. `install`Özniteliği ise `false` , `minimumRequiredVersion` ayarlanmamalıdır. |
| `mapFileExtensions` | İsteğe bağlı. Varsayılan olarak olur `false` . Eğer `true` , dağıtımdaki tüm dosyaların. deploy uzantısı olmalıdır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , bu uzantıyı Web sunucusundan indirdiği anda bu dosyaların dışına çıkaracaktır. Kullanarak uygulamanızı yayımlarsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bu uzantıyı otomatik olarak tüm dosyalara ekler. Bu parametre, bir dağıtım içindeki tüm dosyaların, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . exe gibi "güvenli olmayan" uzantılar ile biten dosyaların aktarımını engelleyen bir Web sunucusundan indirilmesine izin verir. |
| `disallowUrlActivation` | İsteğe bağlı. Varsayılan olarak olur `false` . `true`, Yüklü bir UYGULAMANıN URL 'ye tıklanması veya URL 'Yi Internet Explorer 'a girerek başlatılmasını önler. `install`Özniteliği yoksa, bu öznitelik yoksayılır. |
| `trustURLParameters` | İsteğe bağlı. Varsayılan olarak olur `false` . İse `true` , URL 'nin uygulamaya geçirilen sorgu dizesi parametreleri içermesini sağlar ve komut satırı bağımsız değişkenleri bir komut satırı uygulamasına geçirilir. Daha fazla bilgi için bkz. [nasıl yapılır: sorgu dizesi bilgilerini bir çevrimiçi ClickOnce uygulamasında alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> `disallowUrlActivation`Özniteliği ise `true` , `trustUrlParameters` bildirimden dışlanması ya da açıkça olarak ayarlanması gerekir `false` . |

 `deployment`Öğesi de aşağıdaki alt öğeleri içerir.

## <a name="subscription"></a>aboneliği
 İsteğe bağlı. Öğesini içerir `update` . `subscription`Öğesinde hiç öznitelik yok. `subscription`Öğe yoksa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama güncelleştirmeleri hiçbir şekilde taramayacaktır. `install` `deployment` Öğesinin özniteliği ise, `false` `subscription` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ağdan başlatılan bir uygulama her zaman en son sürümü kullandığından, öğe yok sayılır.

## <a name="update"></a>update
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `subscription` ve ya da öğesini içerir `beforeApplicationStartup` `expiration` . `beforeApplicationStartup``expiration`aynı dağıtım bildiriminde her ikisi de belirtilemez.

 `update`Öğesinde hiç öznitelik yok.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 İsteğe bağlı. Bu öğe, öğesinin bir alt öğesidir `update` ve özniteliği yoktur. `beforeApplicationStartup`Öğe mevcut olduğunda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] istemci çevrimiçi ise güncelleştirmeleri denetlediğinde uygulama engellenir. Bu öğe yoksa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önce öğe için belirtilen değerlere göre güncelleştirmeleri tarar `expiration` . `beforeApplicationStartup``expiration`aynı dağıtım bildiriminde her ikisi de belirtilemez.

## <a name="expiration"></a>dolmadan
 İsteğe bağlı. Bu öğe, öğesinin bir alt öğesidir `update` ve alt öğesi yoktur. `beforeApplicationStartup``expiration`aynı dağıtım bildiriminde her ikisi de belirtilemez. Güncelleştirme denetimi gerçekleştiğinde ve güncelleştirilmiş bir sürüm algılandığında, varolan sürüm çalışırken yeni sürüm önbelleğe alınır. Yeni sürüm daha sonra uygulamanın bir sonraki başlatmaya yüklenir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 `expiration`Öğesi aşağıdaki öznitelikleri destekler.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`maximumAge`|Gereklidir. Uygulamanın bir güncelleştirme denetimi gerçekleştirmeden önce geçerli güncelleştirmenin ne kadar eski olması gerektiğini tanımlar. Zaman birimi özniteliğe göre belirlenir `unit` .|
|`unit`|Gereklidir. İçin zaman birimini tanımlar `maximumAge` . Geçerli birimler `hours` , `days` , ve `weeks` .|

## <a name="deploymentprovider"></a>deploymentProvider
 .NET Framework 2,0 için, dağıtım bildirimi bir bölüm içeriyorsa bu öğe gereklidir `subscription` . .NET Framework 3,5 ve üzeri için, bu öğe isteğe bağlıdır ve varsayılan olarak dağıtım bildiriminin bulunduğu sunucu ve dosya yoludur.

 Bu öğe, öğesinin bir alt öğesidir `deployment` ve aşağıdaki özniteliğe sahiptir.

| Öznitelik | Açıklama |
|------------| - |
| `codebase` | Gereklidir. Uygulamayı güncelleştirmek için kullanılan dağıtım bildiriminin bir Tekdüzen Kaynak tanımlayıcısı (URI) olarak konumunu tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu öğe Ayrıca, CD tabanlı yüklemeler için güncelleştirme konumlarına iletme olanağı tanır. Geçerli bir URI olmalıdır. |

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanızı başlangıçta güncelleştirmeleri tarayacak, başlangıçtan sonra güncelleştirmeleri taratın veya güncelleştirmeleri hiçbir şekilde denetbir şekilde kontrol edebilirsiniz. Başlangıçta güncelleştirmeleri taramak için öğesinin `beforeApplicationStartup` altında bulunduğundan emin olun `update` . Başlangıçtan sonra güncelleştirmeleri taramak için, öğesinin `expiration` öğesinin altında mevcut olduğundan `update` ve bu güncelleştirme aralıklarının sağlandığından emin olun.

 Güncelleştirme denetimini devre dışı bırakmak için öğesini kaldırın `subscription` . Güncelleştirmeleri hiçbir zaman taramayacak dağıtım bildiriminde belirttiğinizde, yöntemini kullanarak güncelleştirmeleri el ile denetleyebilirsiniz <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> .

 DeploymentProvider 'ın güncelleştirmelerle nasıl ilişkili olduğu hakkında daha fazla bilgi için bkz. [ClickOnce Update stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Örnekler
 Aşağıdaki kod örneğinde bir `deployment` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Örnek, `deploymentProvider` tercih edilen güncelleştirme konumunu belirtmek için bir öğesi kullanır.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)