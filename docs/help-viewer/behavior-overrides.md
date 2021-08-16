---
title: Help Content Manager geçersiz kılmaları
description: IDE'de Yardım Görüntüleyicisi'nin varsayılan davranışını ve yardımla ilgili özellikleri değiştiren Yardım İçerik Yöneticisi geçersiz Visual Studio öğrenin.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 8d0838b648a08f430bbe917c9ec073b2760dfe0605f13a83a6ced5ef3e32040f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358668"
---
# <a name="help-content-manager-overrides"></a>Help Content Manager geçersiz kılmaları

IDE'de Yardım Görüntüleyicisi'nin ve yardımla ilgili özelliklerin varsayılan Visual Studio değiştirebilirsiniz. Bazı seçenekler, çeşitli kayıt defteri anahtar [değerlerini ayarlamak için bir .pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) dosyası oluşturarak belirtilir. Diğerleri doğrudan kayıt defterinde ayarlanır.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>.pkgdef dosyası kullanarak Yardım Görüntüleyicisi davranışını denetleme

1. olarak ilk *satırı olan bir .pkgdef* dosyası `[$RootKey$\Help]` oluşturun.

2. Aşağıdaki tabloda açıklanan kayıt defteri anahtar değerlerinin herhangi birini veya hepsini, örneğin, ayrı satırlara `"UseOnlineHelp"=dword:00000001` ekleyin.

3. Dosyayı *%ProgramFiles(x86)%\Microsoft Visual Studio\2017<edition \\ \> \Common7\IDE\CommonExtensions dizinine kopyalayın.*

4. Geliştirici `devenv /updateconfiguration` komut isteminde komutunu çalıştırın.

### <a name="registry-key-values"></a>Kayıt defteri anahtar değerleri

|Kayıt defteri anahtarı değeri|Tür|Veriler|Açıklama|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<http URL for service endpoint\>|Benzersiz bir hizmet uç noktası tanımlama|
|UseOnlineHelp|Dword|`0` çevrimiçi Yardım belirtmek için `1` yerel Yardım belirtmek için|Çevrimiçi veya çevrimdışı yardım varsayılanı tanımlama|
|OnlineBaseUrl|string|\<http URL for service endpoint\>|Benzersiz bir F1 uç noktası tanımlama|
|OnlineHelpPreferenceDisabled|Dword|`0` çevrimiçi Yardım tercihi `1` seçeneğini etkinleştirmek veya devre dışı bırakmak için|Çevrimiçi Yardım tercihini devre dışı bırak seçeneği|
|DisableManageContent|Dword|`0` Yardım Görüntüleyicisi'nde `1` İçeriği Yönet sekmesini etkinleştirmek **veya** devre dışı bırakmak için|İçeriği Yönet **sekmesini devre dışı** bırakma|
|DisableFirstRunHelpSelection|Dword|`0`İlk kez yapılandırılan yardım özelliklerini etkinleştirmek veya devre dışı `1` bırakmak Visual Studio|İlk başlatma sırasında içeriğin yüklemesini devre dışı Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Örnek .pkgdef dosyası içeriği

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Yardım Görüntüleyicisi davranışını değiştirmek için Kayıt Defteri Düzenleyicisi'ni kullanma

Kayıt Defteri Düzenleyicisi'nde kayıt defteri anahtarı değerleri ayarlanacak şekilde aşağıdaki iki davranış denetlenebilirsiniz.

|Görev|Kayıt Defteri Anahtarı|Değer|Veriler|
|----------|-----|------|----|
|BITS iş önceliğini geçersiz kılma|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (64 bit makinede)\Microsoft\Help\v2.3|BITSPriority|**ön plan**, **yüksek,** **normal** veya **düşük**|
|Ağ paylaşımında yerel içerik deposuna işaret edin|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım Görüntüleyicisi yönetici kılavuzu](../help-viewer/administrator-guide.md)
- [Yardım İçerik Yöneticisi için komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)