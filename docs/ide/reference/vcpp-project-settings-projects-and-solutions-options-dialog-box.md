---
title: C++ Project Ayarlar seçenekleri
description: Günlüğe kaydetme, performans Project Ayarlar dosya türleriyle ilgili C++ derleme ve proje ayarlarını tanımlamak için Projeler ve Çözümler bölümündeki VC++ derleme sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 37245bdf8d73d11980951697d63ac18689c161aa8aa2af3f0bbee06f405200a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411990"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu

Bu iletişim kutusu günlüğe kaydetme, performans ve destek dosya türleriyle ilgili C++ derleme ve proje ayarlarını tanımlamaya olanak sağlar.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. Projeler **ve Çözümler'i** ve ardından **VC++ Project Ayarlar.**

## <a name="build-logging"></a>Derleme Günlüğü

 **Evet**

  Derleme günlük dosyasının neslini açma. Bu seçenekBuildLog.htm projenin ara dosyalar dizininde buluna bir dizin oluşturması sağlar. Her yeni derleme önceki dosyanın üzerine BuildLog.htm olur.

 **Hayır**

  Derleme günlük dosyasının neslini kapatma.

## <a name="show-environment-in-log"></a>Ortamı Günlükte Göster

 **Evet**

Derleme günlüğü dosyasındaki ortam değişkenlerini listeler. Bu seçenek, C++ projelerinin derlemeleri sırasında tüm ortam değişkenlerini derleme günlük dosyasına yankılaydıracak şekilde belirtir.

 **Hayır**

Ortam değişkenlerini derleme günlük dosyasından dışlama.

## <a name="build-timing"></a>Derleme Zamanlaması

 **Evet**

  Derleme zamanlamasını okur. Seçilirse, derlemenin tamamlanması için gereken süre Çıkış penceresine yayınlanır. Daha fazla bilgi için [bkz. Çıkış Penceresi.](../../ide/reference/output-window.md)

 **Hayır**

Derleme zamanlamasını kapatma.

## <a name="maximum-concurrent-c-compilations"></a>En fazla eşzamanlı C++ derlemesi

Paralel C++ derlemesi için en fazla CPU çekirdeği sayısını belirtir.

## <a name="extensions-to-include"></a>Dahil Etmek Için Uzantılar

Projenize taşınabilir dosyaların dosya adı uzantılarını belirtir.

## <a name="extensions-to-hide"></a>Gizlenen Uzantılar

Tüm Dosyaları Göster etkinleştirildiğinde, dosya adı **uzantılarını Çözüm Gezgini** **dosyalarda görüntülenmez.**

## <a name="build-customization-search-path"></a>Özelleştirme Arama Yolu Oluşturma

Projeleriniz için derleme kuralları tanımlamanıza yardımcı olan .rules dosyalarını içeren dizinlerin listesini belirtir.

## <a name="solution-explorer-mode"></a>Çözüm Gezgini Modu

**Projede yalnızca dosyaları göster**

Dosyaları **Çözüm Gezgini** projesinde görüntülemek için yapılandırıyor.

**Tüm dosyaları göster**

Proje **Çözüm Gezgini** proje klasöründeki dosyaları ve diskte dosyaları gösterecek şekilde yapılandırma.

## <a name="enable-project-caching"></a>Project Önbelleğe Alma

**Evet**

Projeyi Visual Studio yeniden derlemek yerine önbelleğe alınan verileri yükleyemediklerinden, proje verilerini önbelleğe alamalarını sağlar. Önbelleğe alınmış verilerin kullanımı proje yükleme sürelerini önemli ölçüde hızlandırabilir.

**Hayır**

Önbelleğe alınmış proje verilerini kullanma. Proje her yüklenirken proje dosyalarını ayrıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ Programları Oluşturma](/cpp/build/projects-and-build-systems-cpp)
- [C/C++ Oluşturma Başvurusu](/cpp/build/reference/c-cpp-building-reference)