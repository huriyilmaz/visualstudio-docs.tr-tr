---
title: Genel sekmesi, pencere özellikleri Iletişim kutusu | Microsoft Docs
description: Resim yazısı, tanıtıcı, dikdörtgen, uygulama örneği tutamacı, menü tanıtıcısı ve Kullanıcı verileri dahil olmak üzere bir pencere hakkında bilgi için Genel sekmesini görüntüleyin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce5dda5f3fb1581e5239d9d3ffcdee8de864498a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154310"
---
# <a name="general-tab-window-properties-dialog-box"></a>Genel Sekme, Pencere Özellikleri İletişim Kutusu
Seçili pencereyle ilgili bilgileri göstermek için **genel** sekmesini kullanın. [pencere özellikleri iletişim kutusunu](../debugger/window-properties-dialog-box.md)görüntülemek için odağı [Windows görünümü](../debugger/windows-view.md) penceresine taşıyın. Ağaçta herhangi bir pencere düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

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