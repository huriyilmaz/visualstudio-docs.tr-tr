---
title: Yardım Içerik Yöneticisi geçersiz kılmaları
description: Yardım Görüntüleyicisi 'nin varsayılan davranışını ve Visual Studio IDE 'deki yardım ile ilgili özellikleri değiştiren yardım Içerik Yöneticisi geçersiz kılmaları hakkında bilgi edinin.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f9c9a950156f29bda68a134af2eb299b3431445f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944296"
---
# <a name="help-content-manager-overrides"></a>Yardım Içerik Yöneticisi geçersiz kılmaları

Visual Studio IDE 'deki Yardım Görüntüleyicisi ve yardım ile ilgili özelliklerin varsayılan davranışını değiştirebilirsiniz. Bazı seçenekler, çeşitli kayıt defteri anahtarı değerlerini ayarlamak için bir [. pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) dosyası oluşturularak belirtilir. Diğerleri kayıt defterinde doğrudan ayarlanır.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Bir. pkgdef dosyası kullanarak Yardım Görüntüleyicisi davranışını denetleme

1. İle ilk satırı içeren bir *. pkgdef* dosyası oluşturun `[$RootKey$\Help]` .

2. Aşağıdaki tabloda açıklanan kayıt defteri anahtarı değerlerinin tümünü veya tümünü ayrı satırlarda ekleyin, örneğin `"UseOnlineHelp"=dword:00000001` .

3. Dosyayı *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\<Edition \> \Common7\IDE\CommonExtensions*'e kopyalayın.

4. `devenv /updateconfiguration`Bir geliştirici komut isteminde çalıştırın.

### <a name="registry-key-values"></a>Kayıt defteri anahtarı değerleri

|Kayıt defteri anahtarı değeri|Tür|Veriler|Description|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<http URL for service endpoint\>|Benzersiz bir hizmet uç noktası tanımlama|
|UseOnlineHelp|ekleyebileceği|`0` yerel yardım 'ı belirtmek için, `1` çevrimiçi yardım belirtme|Çevrimiçi veya çevrimdışı yardım varsayılanını tanımlama|
|OnlineBaseUrl 'Si|string|\<http URL for service endpoint\>|Benzersiz bir F1 uç noktası tanımlama|
|OnlineHelpPreferenceDisabled|ekleyebileceği|`0``1`çevrimiçi yardım tercihi seçeneğini etkinleştirmek veya devre dışı bırakmak için|Çevrimiçi yardım tercih seçeneğini devre dışı bırak|
|DisableManageContent|ekleyebileceği|`0``1`Yardım Görüntüleyicisi 'Nde **İçeriği Yönet** sekmesini etkinleştirmek veya devre dışı bırakmak için|**Içeriği Yönet** sekmesini devre dışı bırak|
|DisableFirstRunHelpSelection|ekleyebileceği|`0``1`Visual Studio ilk kez başlatıldığında yapılandırılmış yardım özelliklerini etkinleştirmek veya devre dışı bırakmak için|Visual Studio 'nun ilk başlatıldığında içerik yüklemeyi devre dışı bırak|

### <a name="example-pkgdef-file-contents"></a>Örnek. pkgdef dosya içeriği

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Yardım Görüntüleyicisi davranışını değiştirmek için kayıt defteri Düzenleyicisi 'ni kullanma

Aşağıdaki iki davranış kayıt defteri düzenleyicisinde kayıt defteri anahtarı değerleri ayarlanarak denetlenebilir.

|Görev|Kayıt Defteri Anahtarı|Değer|Veriler|
|----------|-----|------|----|
|BITS iş önceliğini geçersiz kıl|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (64 bitlik bir makinede) \Microsoft\help\v2,3|Bitspriınlık|**ön plan**, **yüksek**, **normal** veya **düşük**|
|Ağ paylaşımındaki yerel içerik deposuna işaret edin|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v 2.3 \ Catalogs\VisualStudio15|LocationPath|"*Contentstorenetworkshare*"|

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md)
- [Yardım Içeriği Yöneticisi için komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)