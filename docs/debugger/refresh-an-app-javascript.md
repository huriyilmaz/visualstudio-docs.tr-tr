---
title: UWP uygulamasını yenileme | Microsoft Docs
description: hata ayıklarken kodunuzda değişiklik yapın ve Visual Studio JavaScript kullanarak bir Evrensel Windows Platformu (UWP) uygulamasını yenileyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 9beb9a96b64d9ad60e6aba1a407bdddb11f61ee1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112509"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Visual Studio bir UWP uygulamasını yenileme

 hata ayıklarken kodunuzda değişiklikler yapabilir ve sonra **hata ayıklama** araç çubuğundaki **Windows uygulamayı yenile** düğmesini seçerek JavaScript kullanarak UWP uygulamasını yenileyebilirsiniz. Bu düğmenin belirlenmesi, hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamayı yeniden yükler. Yenile özelliği, HTML, CSS ve JavaScript kodunu değiştirmenize ve sonucu hızla görebilmenizi sağlar. Bu özellik UWP uygulamaları için desteklenir.

 Yenileme, uygulamanızın durumunu korumaz veya uygulamanızda aşağıdaki değişiklikleri yansıtmaz:

- Paket bildiriminde belirtilen görüntülerde yapılan değişiklikler dahil olmak üzere Paket bildirim dosyası değişiklikleri.

- bir SDK başvurusu ekleme veya kaldırma veya Windows Çalışma Zamanı bileşenlerinde değişiklikler (. winmd dosyaları) gibi başvuru değişiklikleri.

- . Resjson dosyalarındaki dizelerdeki değişiklikler gibi kaynak değişiklikleri.

- yol adı değişiklikleri, yeni proje dosyaları veya silinen dosyalar ile sonuçlanan dosya değişikliklerini Project.

- seçilen hata ayıklama cihazında yapılan değişiklikler veya bir dosya için paket eyleminde yapılan değişiklikler gibi Project ve öğe özelliği değişiklikleri (Özellikler penceresi).

> [!IMPORTANT]
> Başvuruları değiştirdiğinizde, paket bildirimini değiştirdiğinizde veya yukarıdaki listede başka değişiklikler yaparsanız, HTML, CSS ve JavaScript kaynak dosyalarını güncelleştirmek için hata ayıklayıcıyı durdurup yeniden başlatmanız gerekir.

### <a name="to-refresh-an-app"></a>Bir uygulamayı yenilemek için

1. UWP projeniz Visual Studio açıkken, hata ayıklama hedefi olarak **yerel makine** ' yi seçin.

     ![Hata ayıklama hedef listesini seçin](../debugger/media/js_select_target.png "JS_Select_Target")

3. Uygulamayı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.

4. Visual Studio geçiş yapın.

5. UWP uygulamanızın giriş sayfasında, bazı HTML 'yi düzenleyin.

7. şu şekilde görünen **Windows uygulamayı yenile** düğmesine tıklayın: ![Windows uygulamayı yenile düğmesi](../debugger/media/js_refresh.png "JS_Refresh"). (Veya F4 tuşuna basın.)

8. Uygulamaya geçiş yapın. Uygulama yeniden yüklenir ve güncelleştirilmiş HTML, uygulamayı işlemek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)