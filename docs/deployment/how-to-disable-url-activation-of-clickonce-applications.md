---
title: ClickOnce uygulamalarının URL etkinleştirmesini devre dışı bırak
description: kullanıcıların uygulamayı Başlat menüsü başlatmasını istemeniz durumunda ClickOnce uygulamanız için otomatik başlatmayı devre dışı bırakmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b8f1ca13c784e9d8d74b9de4420c92c55cf7cf16
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035858"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>nasıl yapılır: ClickOnce uygulamaların URL etkinleştirmeyi devre dışı bırakma

Genellikle, bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bir Web sunucusundan yüklendikten hemen sonra otomatik olarak başlatılır. Güvenlik nedenleriyle, bu davranışı devre dışı bırakmayı ve kullanıcılara bunun yerine başlangıç menüsünden uygulamayı **başlatmasını** söylemeniz gerekebilir. Aşağıdaki yordamda URL etkinleştirmeyi devre dışı bırakma açıklanmaktadır.

Bu teknik, yalnızca [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanıcının bilgisayarında bir Web sunucusundan yüklenen uygulamalar için kullanılabilir. Yalnızca kendi URL 'SI kullanılarak başlatılabilen, yalnızca çevrimiçi uygulamalar için kullanılamaz. yalnızca çevrimiçi ve yüklü uygulamalar arasındaki fark hakkında daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).

bu yordam, MageUI.exe Windows yazılım geliştirme seti (SDK) aracını kullanır. bu araç hakkında daha fazla bilgi için bkz. [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Bu yordamı, Visual Studio kullanarak da gerçekleştirebilirsiniz.

## <a name="procedure"></a>Yordam

### <a name="to-disable-url-activation-for-your-application"></a>Uygulamanız için URL etkinleştirmeyi devre dışı bırakmak için

1. Dağıtım bildiriminizi MageUI.exe ' de açın. henüz bir tane oluşturmadıysanız [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)' daki adımları izleyin.

2. **Dağıtım seçenekleri** sekmesini seçin.

3. **Yüklendikten sonra otomatik olarak uygulamayı çalıştır** onay kutusunu temizleyin.

4. Bildirimi kaydedin ve imzalayın.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)