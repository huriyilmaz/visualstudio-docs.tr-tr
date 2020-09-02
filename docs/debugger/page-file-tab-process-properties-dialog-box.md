---
title: Sayfa dosyası sekmesi, Işlem özellikleri Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25dc3b0aca1b58c18ae4038540c14fc4dbfe4036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904113"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Sayfa Dosyası Sekmesi, İşlem Özellikleri İletişim Kutusu
Bir işlemin sayfalama dosyasını incelemek için **sayfa dosyası** sekmesini kullanın. [Işlem özellikleri Iletişim kutusunu](../debugger/process-properties-dialog-box.md)görüntülemek için odağı bir [işlem görünümü](../debugger/processes-view.md) penceresine taşıyın. Ağaçta herhangi bir işlem düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 Aşağıdaki ayarlar **sayfa dosyası** sekmesinde bulunur:

|Giriş|Açıklama|
|-----------|-----------------|
|**Sayfa dosyası baytları**|Bu işlemin sayfalama dosyasında kullandığı geçerli sayfa sayısı. Sayfalama dosyası, işlem tarafından kullanılan ancak diğer dosyalarda bulunmayan veri sayfalarını depolar. Disk belleği dosyası tüm süreçler tarafından kullanılır ve disk belleği dosyasında boşluk olmaması, diğer işlemlerin çalıştığı sırada hatalara neden olabilir.|
|**Yoğun sayfa dosyası baytları**|Bu işlemin sayfalama dosyasında kullandığı en fazla sayfa sayısı.|
|**Sayfa hataları**|Bu işlemde yürütülen iş parçacıklarının sayfa hatası sayısı. Bir iş parçacığı, ana bellekteki çalışma kümesinde olmayan bir sanal bellek sayfasına başvurduğunda bir sayfa hatası oluşur. Bu nedenle, sayfa bekleme listeteyse ve bu nedenle zaten ana bellekteyse veya sayfanın paylaşıldığı başka bir işlem tarafından kullanılıyorsa, sayfa diskten alınmayacak.|