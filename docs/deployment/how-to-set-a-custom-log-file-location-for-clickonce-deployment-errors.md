---
title: özel günlük dosyası konumu ayarlama (ClickOnce dağıtım hataları)
description: tüm dağıtımlar için ClickOnce, ClickOnce dağıtımını yükleme ve başlatma hatalarını belgelemek için gereken etkinleştirme günlük dosyaları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 94786783ebc4ccf849af122b7c334f9543f72435
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073831"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>nasıl yapılır: ClickOnce dağıtım hataları için özel günlük dosyası konumu ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tüm dağıtımlar için etkinleştirme günlük dosyalarını tutar. Bu Günlükler, bir dağıtımı yükleme ve başlatma ile ilgili tüm hataları belgeleyin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] her dağıtım etkinleştirmesi için bir günlük dosyası oluşturur. Bu günlük dosyalarını Temporary Internet Files klasöründe depolar. Bir dağıtım için günlük dosyası, bir etkinleştirme hatası oluştuğunda kullanıcıya gösterilir ve Kullanıcı ortaya çıkan hata iletişim kutusunda **Ayrıntılar** ' a tıklar.

 Özel bir günlük dosyası yolu ayarlamak için, kayıt defteri Düzenleyicisi 'Ni (**regedit.exe**) kullanarak belirli bir istemci için bu davranışı değiştirebilirsiniz. Bu durumda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tek bir dosyadaki tüm dağıtımlar için etkinleştirme başarıları ve başarısızlıklarını günlüğe kaydeder.

> [!CAUTION]
> Kayıt Defteri Düzenleyicisi 'Ni yanlış kullanırsanız, işletim sisteminizi yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilirsiniz. Kayıt Defteri Düzenleyicisi 'Ni kullanarak kendi sorumluluğunuzdadır.

> [!NOTE]
> Büyük bir zaman büyümesini engellemek için günlük dosyasını kesmeniz veya silmeniz gerekir.

 Aşağıdaki yordamda, tek bir istemci için özel bir günlük dosyası konumunun nasıl ayarlanacağı açıklanmaktadır.

### <a name="to-set-a-custom-log-file-location"></a>Özel bir günlük dosyası konumu ayarlamak için

1. **Regedit.exe** açın.

2. Düğüme gidin `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Dize değerini `LogFilePath` tercih ettiğiniz özel günlük konumunun tam yolu ve dosya adı olarak ayarlayın.

     Bu konum, kullanıcının yazma erişimine sahip olduğu bir dizinde olmalıdır. örneğin, Windows Vista 'da aşağıdaki klasör yapısını oluşturun ve `LogFilePath` *C:\Users \\ \<username> \ documents\logs\ ClickOnce \ınstalyükleme.log* olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)