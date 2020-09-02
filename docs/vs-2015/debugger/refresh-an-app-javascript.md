---
title: Bir uygulamayı yenileme (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8be97212f4510002a78e6565fc9884930db89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808021"
---
# <a name="refresh-an-app-javascript"></a>Uygulamayı yenileme (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Hata ayıklarken kodunuzda değişiklik yapabilir ve sonra **hata ayıklama** araç çubuğundaki **Windows uygulamasını Yenile** düğmesini seçerek JavaScript kullanarak bir mağaza uygulamasını yenileyebilirsiniz. Bu düğmenin belirlenmesi, hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamayı yeniden yükler. Yenile özelliği, HTML, CSS ve JavaScript kodunu değiştirmenize ve sonucu hızla görebilmenizi sağlar. Bu özellik hem Windows Mağazası hem de Windows Phone Mağazası uygulamaları için desteklenir.  
  
 Yenileme, uygulamanızın durumunu korumaz veya uygulamanızda aşağıdaki değişiklikleri yansıtmaz:  
  
- Paket bildiriminde belirtilen görüntülerde yapılan değişiklikler dahil olmak üzere Paket bildirim dosyası değişiklikleri.  
  
- Bir SDK başvurusu ekleme veya kaldırma veya Windows Çalışma Zamanı bileşenlerinde değişiklikler (. winmd dosyaları) gibi başvuru değişiklikleri.  
  
- . Resjson dosyalarındaki dizelerdeki değişiklikler gibi kaynak değişiklikleri.  
  
- Yol adı ile sonuçlanan proje dosyası değişiklikleri, yeni proje dosyaları veya silinen dosyalar.  
  
- Seçilen hata ayıklama cihazında yapılan değişiklikler veya bir dosya için paket eyleminde yapılan değişiklikler gibi proje ve öğe özelliği değişiklikleri (Özellikler penceresi).  
  
> [!IMPORTANT]
> Başvuruları değiştirdiğinizde, paket bildirimini değiştirdiğinizde veya yukarıdaki listede başka değişiklikler yaparsanız, HTML, CSS ve JavaScript kaynak dosyalarını güncelleştirmek için hata ayıklayıcıyı durdurup yeniden başlatmanız gerekir.  
  
### <a name="to-refresh-an-app"></a>Bir uygulamayı yenilemek için  
  
1. Visual Studio 'da, gezinti uygulaması proje şablonunu kullanarak yeni bir proje oluşturun.  
  
     Bu, Windows Mağazası uygulaması, Windows Phone Mağazası uygulaması veya evrensel bir uygulama olabilir.  
  
2. Visual Studio 'da şablon açıkken bir hata ayıklama hedefi seçin.  
  
     Geçerli başlangıç projeniz bir Windows Phone projesi ise, hata ayıklama hedefi için bir Windows Phone öykünücü seçin. Aksi takdirde, **simülatör** veya **yerel makine**' yi seçin.  
  
     ![Hata ayıklama hedef listesini seçin](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Uygulamayı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
4. Visual Studio 'ya geçiş yapın. (F12 tuşuna basın.)  
  
5. **Çözüm Gezgini**, **Sayfalar**  >  **giriş** klasöründe home.html ' yi açın.  
  
6. Sayfa başlığı metnini Değiştir  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     Bunun gibi başka bir şey için:  
  
    ```html  
    Hello!  
    ```  
  
7. Windows uygulamasını **Yenile** düğmesine tıklayın ve şuna benzer: ![Windows uygulamasını Yenile düğmesi](../debugger/media/js-refresh.png "JS_Refresh"). (Veya F4 tuşuna basın.)  
  
8. Uygulamaya geçiş yapın. Uygulama, hata ayıklayıcı yeniden başlatılmadan yeniden yüklenir ve yeni sayfa başlığı görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)
