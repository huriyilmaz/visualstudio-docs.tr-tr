---
title: COM Sunucusu ve Kapsayıcı Hata Ayıklama | Microsoft Docs
description: COM sunucusu ve kapsayıcı hata ayıklama hakkında bilgi edinebilirsiniz. Aynı çözümde, kapsayıcı bilgileri olmayan bir sunucu uygulamasında veya bir SDI uygulamasında COM sunucusu ve kapsayıcıda hata ayıklama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 89613dbc80a4a83fe1cd6a8303b43f863daea272
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803732"
---
# <a name="com-server-and-container-debugging"></a>COM Sunucusunda ve Kapsayıcısında Hata Ayıklama
COM uygulamaları, programcının doğrudan denetimi dışında bir dizi görev gerçekleştirmektedir. URL'ler arasındaki iletişim, nesnelerdeki kullanım sayıları ve Pano işlemleri, beklenmeyen davranışlarla karşılaşabilirsiniz alanlardan yalnızca birkaçıdır. Bu durumda ilk adımınız sorunun kaynağını izlemek olur.

 Hata Visual Studio kapsayıcılar ve sunucular arasında adımlamayı destekler. Bu, uzak yordam çağrıları (RPC) arasında adım adım atabilmeyi içerir.

## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> Aynı Çözümde COM Sunucusu ve Kapsayıcıda Hata Ayıklama
 Aynı çözüm içindeki iki proje kullanarak bir COM sunucusu ve kapsayıcıda hata ayıkabilirsiniz. Her projede uygun kesme noktaları ayarlama ve hata ayıklama. Kapsayıcı bir kesme noktasıyla karşılaşan sunucuya bir çağrıda olduğunda, kapsayıcı sunucu kodu dönene kadar bekler (yani hata ayıklamayı bitirene kadar).

 COM kapsayıcısı hata ayıklaması, standart bir programda hata ayıklamaya benzer. Bir fark, geri arama oluşturan bir olayda hata ayıklamaktır (örneğin, kapsayıcı uygulamasının üzerine veri sürükleme). Bu durumda, geri çağırma işlevinde bir kesme noktası ayarlamalısiniz.

## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Kapsayıcı Bilgisi Olmadan Sunucu Uygulamasında Hata Ayıklama
 Kapsayıcı uygulamanız için hata ayıklama bilgilerine sahip değil veya kullanmak istemiyorsanız, sunucu uygulamasında hata ayıklamaya başlama üç adımlı bir işlemdir:

1. Normal bir uygulama olarak sunucuda hata ayıklamaya başlama.

2. Kesme noktaları istediğiniz gibi ayarlayın.

3. Kapsayıcı uygulamasını başlatma.

## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Sunucu ve Etki Alanı Yalıtımı (SDI) Uygulamasında Hata Ayıklama
 Bir SDI sunucu uygulamasında hata ayıklarsanız, `/Embedding` `/Automation` C/C++, C#  veya Visual Basic projeleri için *Project* Özellik Sayfaları iletişim kutusunda Komut satırı bağımsız değişkenleri özelliğini belirtmeniz Visual Basic gerekir.

 Bu komut satırı bağımsız değişkenleriyle, hata ayıklayıcı sunucu uygulamasını bir kapsayıcıdan başlatıldı gibi başlatabilirsiniz. Kapsayıcıyı Program Yöneticisi'nde veya Dosya Yöneticisi'nde başlatmanız, kapsayıcının hata ayıklayıcıda başlatan sunucu örneğini kullanmalarına neden olur.

 Project *Sayfaları* iletişim kutusuna erişmek için, Çözüm Gezgini projenize sağ tıklayın ve ardından kısayol menüsünden Özellikler'i seçin. Komut satırı bağımsız değişkenleri özelliğini bulmak için Yapılandırma Özellikleri kategorisini genişletin ve Hata Ayıklama sayfasına tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [COM ve ActiveX Hata Ayıklama](../debugger/com-and-activex-debugging.md)