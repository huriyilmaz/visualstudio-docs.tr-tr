---
title: Genel sekmesi, pencere özellikleri Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5160c79e2c8dae474927e6af7ebdc9e371e9edc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62849567"
---
# <a name="general-tab-window-properties-dialog-box"></a>Genel Sekme, Pencere Özellikleri İletişim Kutusu
Seçili pencereyle ilgili bilgileri göstermek için **genel** sekmesini kullanın. [Pencere özellikleri Iletişim kutusunu](../debugger/window-properties-dialog-box.md)görüntülemek Için odağı [Windows görünümü](../debugger/windows-view.md) penceresine taşıyın. Ağaçta herhangi bir pencere düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 **Genel** sekmesinde aşağıdaki ayarlar kullanılabilir:

|Giriş|Açıklama|
|-----------|-----------------|
|**Pencere başlığı**|Pencere başlığında bulunan metin veya bir denetim ise bir pencerede bulunan metin.|
|**Pencere tutamacı**|Bu pencerenin benzersiz KIMLIĞI. Pencere tanıtıcı numaraları yeniden kullanılır; yalnızca söz konusu pencerenin ömrü için bir pencere belirler.|
|**Pencere proc**|Bu pencere için pencere yordamı işlevinin sanal adresi. Bu alan Ayrıca bu pencerenin bir Unicode penceresi olup olmadığını ve alt sınıflandırılmadığını gösterir.|
|**Dikdörtgen**|Pencere için sınırlayıcı dikdörtgen. Dikdörtgenin boyutu da görüntülenir. Birimler Ekran koordinatlarındaki piksellerdir.|
|**Geri yüklenen Rect**|Geri yüklenen pencere için sınırlayıcı dikdörtgen. Dikdörtgenin boyutu da görüntülenir. Geri yüklenen Rect, yalnızca pencere büyütüldüğünde veya küçültülmüş olduğunda dikdörtgenden farklılık gösterir. Birimler Ekran koordinatlarındaki piksellerdir.|
|**İstemci Rect 'i**|Pencere istemci alanı için sınırlayıcı dikdörtgen. Dikdörtgenin boyutu da görüntülenir. Birimler, pencere istemci alanının sol üst kısmına göre piksellerden oluşur.|
|**Örnek tanıtıcısı**|Uygulamanın örnek tanıtıcısı. Örnek tutamaçları benzersiz değil.|
|**Denetim KIMLIĞI veya menü tanıtıcısı**|Görüntülenmekte olan pencere bir alt pencere ise, denetim KIMLIĞI etiketi görüntülenir. Denetim KIMLIĞI, bu alt pencerenin Denetim KIMLIĞINI tanımlayan bir tamsayıdır. Görüntülenmekte olan pencere bir alt pencere değilse, menü tanıtıcı etiketi görüntülenir. Menü tutamacı, bu pencereyle ilişkili menünün tanıtıcısını tanımlayan bir tamsayıdır.|
|**Kullanıcı verileri**|Bu pencere yapısına ekli uygulamaya özgü veriler.|
|**Pencere baytları**|Bu pencereyle ilişkili ek bayt sayısı. Bu baytların anlamı uygulama tarafından belirlenir. Bayt değerlerini DWORD biçiminde görmek için liste kutusunu genişletin.|