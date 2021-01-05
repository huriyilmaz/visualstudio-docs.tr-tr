---
title: COM sunucusu ve kapsayıcı hata ayıklaması | Microsoft Docs
description: COM sunucusu ve kapsayıcı hata ayıklama hakkında bilgi edinin. Aynı çözümde bir COM sunucusunda ve kapsayıcıda hata ayıklayın, kapsayıcı bilgileri olmayan bir sunucu uygulaması veya bir SDI uygulaması.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b1d4ceecae385ac6e5444c60f6634b260f2e887
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728982"
---
# <a name="com-server-and-container-debugging"></a>COM Sunucusunda ve Kapsayıcısında Hata Ayıklama
COM uygulamaları, programcının doğrudan denetimi dışında çeşitli görevler gerçekleştirir. Dll 'Ler, nesnelerde kullanım sayıları ve Pano işlemlerinde iletişim, beklenmeyen davranışlarla karşılaşabileceğiniz alanlardan yalnızca birkaçı. Bu durumda, ilk adımınız sorunun kaynağını izlemenizde olur.

 Visual Studio hata ayıklayıcı, kapsayıcılar ve sunucular üzerinde ve içinde adımlamayı destekler. Bu, uzak yordam çağrılarında (RPC) adım adım özelliği içerir.

## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> Aynı çözümde bir COM sunucusunda ve kapsayıcıda hata ayıklama
 Aynı çözüm içinde iki proje kullanarak bir COM sunucusunda ve kapsayıcıda hata ayıklaması yapabilirsiniz. Her projede uygun kesme noktaları ayarlayın ve hata ayıklayın. Kapsayıcı, bir kesme noktasına isabet eden sunucuya bir çağrı yaptığında, kapsayıcı sunucu kodu dönene kadar bekler (yani, hata ayıklamayı bitirmeden).

 COM kapsayıcısının hata ayıklaması, Standart programda hata ayıklamaya benzer. Bir fark, geri çağırma üreten bir olayda hata ayıkladığınızda (örneğin, kapsayıcı uygulama üzerinde veri sürükleme). Bu durumda, geri arama işlevinde bir kesme noktası ayarlamanız gerekir.

## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Kapsayıcı bilgileri olmadan sunucu uygulamasında hata ayıklama
 Kapsayıcı uygulamanız için hata ayıklama bilgilerini kullanmak veya istemiyorsanız, sunucu uygulamasında hata ayıklamaya başlamak üç adımlı bir işlemdir:

1. Normal bir uygulama olarak sunucuda hata ayıklamayı başlatın.

2. Kesme noktalarını istediğiniz gibi ayarlayın.

3. Kapsayıcı uygulamasını başlatın.

## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Sunucu ve etki alanı yalıtımı (SDI) uygulamasında hata ayıklama
 Bir SDI Sunucu uygulamasında hata ayıklaması yapıyorsanız, `/Embedding` `/Automation` C/C++, C# veya Visual Basic projeleri için *Proje* Özellik sayfaları iletişim kutusundaki **komut satırı bağımsız değişkenleri** özelliğini belirtmeniz gerekir.

 Bu komut satırı bağımsız değişkenleriyle, hata ayıklayıcı sunucu uygulamasını bir kapsayıcıdan başlatılmış gibi başlatabilir. Kapsayıcının Program Yöneticisi 'nden veya dosya yöneticisinden başlatılması, kapsayıcının hata ayıklayıcıda başlatılan sunucu örneğini kullanmasına neden olur.

 *Proje* Özellik sayfaları iletişim kutusuna erişmek için Çözüm Gezgini ' de projenize sağ tıklayın ve ardından kısayol menüsünden Özellikler ' i seçin. Komut satırı bağımsız değişkenleri özelliğini bulmak için yapılandırma özellikleri kategorisini genişletin ve hata ayıklama sayfasına tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)