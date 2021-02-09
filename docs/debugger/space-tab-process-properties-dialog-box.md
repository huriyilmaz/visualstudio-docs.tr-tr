---
title: Boşluk sekmesi, Işlem özellikleri Iletişim kutusu | Microsoft Docs
description: Hata ayıklama sırasında Spy + + içinde Işlem özellikleri iletişim kutusunu görüntülemeyi öğrenin. Boşluk sekmesinde kullanılabilir olan ayarları gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cb1a33b1456e44b745b3b8992c0233634368952b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903503"
---
# <a name="space-tab-process-properties-dialog-box"></a>Alan Sekmesi, İşlem Özellikleri İletişim Kutusu
Bir işlemin adres alanını incelemek için **boşluk** sekmesini kullanın. [Işlem özellikleri Iletişim kutusunu](../debugger/process-properties-dialog-box.md)görüntülemek için odağı bir [işlem görünümü](../debugger/processes-view.md) penceresine taşıyın. Ağaçta herhangi bir işlem düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 **Boşluk** sekmesinde aşağıdaki ayarlar kullanılabilir:

|Giriş|Description|
|-----------|-----------------|
|**Boşluk olarak işaretlenen alanı göster**|Alan kategorisini (görüntü, eşlenmiş, ayrılmış veya atanmamış) seçmek için bu liste kutusunu kullanın.|
|**Yürütülebilir baytlar**|Seçili Kategori için, bu işlemin kullandığı tüm adres alanı toplamı. Yürütülebilir bellek, programlar tarafından yürütülebilecek, ancak okunmayabilir veya yazılamaz bellektir.|
|**Çalıştırılabilir-salt okunurdur bayt**|Seçili Kategori için, bu işlemin kullandığı salt okuma özellikleriyle birlikte kullanılan tüm adres alanı toplamıdır. Çalıştırılabilir-salt okuma belleği, yürütülebilecek ve okunan bellektir.|
|**Çalıştırılabilir-okuma-yazma baytları**|Seçili Kategori için, bu işlemin kullandığı okuma yazma özellikleriyle birlikte kullanılan tüm adres alanının toplamı. Çalıştırılabilir-okuma-yazma belleği, programlar tarafından ve okuma ve değiştirme için yürütülebilecek bellektir.|
|**Çalıştırılabilir-yazma bayt kopyalama**|Seçili Kategori için, programlar tarafından yürütülebilecek ve okunan ve yazılan tüm adres alanı toplamı. Bu tür bir koruma, belleğin süreçler arasında paylaşılması gerektiğinde kullanılır. Paylaşım işlemi yalnızca belleği okuduklarında, hepsi de aynı belleği kullanır. Paylaşım işlemi yazma erişimini bir şekilde azaldıysanız, bu belleğin bir kopyası işlem için yapılır.|
|**Erişim yok bayt**|Seçili Kategori için, bir işlemin kullanmasını engelleyen tüm adres alanı toplamı. Yazma veya okuma girişiminde bulunulursa bir erişim ihlali oluşturulur.|
|**Salt okuma baytları**|Seçili Kategori için, yürütülebilecek tüm adres alanının toplamı ve okuma.|
|**Okuma-yazma baytları**|Seçili Kategori için, okuma ve yazma olanağı sağlayan tüm adres alanı toplamı.|
|**Yazma/kopyalama baytları**|Seçili Kategori için, bellek paylaşımına okuma için, ancak yazma için izin veren tüm adres alanı toplamı. Süreçler bu belleği okurken aynı belleği paylaşabilir. Ancak, bir paylaşım süreci bu paylaşılan belleğe okuma/yazma erişimi sağlamak istediğinde, bu belleğin bir kopyası yazma için yapılır.|