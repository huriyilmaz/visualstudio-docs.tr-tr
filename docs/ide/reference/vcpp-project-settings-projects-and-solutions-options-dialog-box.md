---
title: C++ proje ayarları seçenekleri
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
ms.openlocfilehash: c7acd0d8f9c6d15f9f20c42f59c3bd5562884ac3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68918891"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu

Bu iletişim kutusu, günlüğe kaydetme, performans ve destekleyici dosya türleriyle ilgili C++ derleme ve proje ayarlarını tanımlamanıza olanak sağlar.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Projeler ve çözümler**' i seçin ve ardından **VC + + proje ayarları**' nı seçin.

## <a name="build-logging"></a>Derleme günlüğü

 **Evet**

  Derleme günlüğü dosyasının oluşturulmasını etkinleştirir. Bu seçenek, projenin ara dosyalar dizininde bulunan BuildLog.htm oluşturur. Her yeni derleme önceki BuildLog.htm dosyanın üzerine yazar.

 **Hayır**

  Derleme günlüğü dosyasının oluşturulmasını devre dışı bırakır.

## <a name="show-environment-in-log"></a>Ortamı günlükte göster

 **Evet**

Yapı günlük dosyasındaki ortam değişkenlerini listeler. Bu seçenek, C++ projelerinin derlemeleri sırasında tüm ortam değişkenlerini derleme günlüğü dosyasına yankılanması gerektiğini belirtir.

 **Hayır**

Ortam değişkenlerini derleme günlük dosyasından hariç tutun.

## <a name="build-timing"></a>Derleme zamanlaması

 **Evet**

  Derleme zamanlamasını etkinleştirir. Seçilirse, derleme işleminin tamamlaması için gereken süre çıkış penceresine gönderilir. Daha fazla bilgi için bkz. [Çıkış penceresi](../../ide/reference/output-window.md).

 **Hayır**

Derleme zamanlamasını kapatır.

## <a name="maximum-concurrent-c-compilations"></a>Maksimum eşzamanlı C++ derlemeleri

Paralel C++ derlemesi için kullanılacak en fazla CPU çekirdeği sayısını belirtir.

## <a name="extensions-to-include"></a>Dahil edilecek uzantılar

Projenizde yer alan dosyaların dosya adı uzantılarını belirtir.

## <a name="extensions-to-hide"></a>Gizlenecek uzantılar

**Tüm dosyaları göster** etkinleştirildiğinde **Çözüm Gezgini** görüntülenmeyen dosyaların dosya adı uzantılarını belirtir.

## <a name="build-customization-search-path"></a>Yapı özelleştirme arama yolu

Projeleriniz için yapı kuralları tanımlamanıza yardımcı olan. Rules dosyalarını içeren dizinlerin listesini belirtir.

## <a name="solution-explorer-mode"></a>Çözüm Gezgini modu

**Yalnızca projedeki dosyaları göster**

Yalnızca projedeki dosyaları göstermek için **Çözüm Gezgini** yapılandırır.

**Tüm dosyaları göster**

Proje klasöründeki dosyaları projede ve diskte göstermek için **Çözüm Gezgini** yapılandırır.

## <a name="enable-project-caching"></a>Proje önbelleğe almayı etkinleştir

**Evet**

Projeyi bir sonraki sefer açtığınızda proje dosyalarından yeniden hesaplama yerine önbelleğe alınmış verileri yükleyebilecekleri için Visual Studio 'Nun proje verilerini önbelleğe almasını sağlar. Önbelleğe alınmış verilerin kullanılması, proje yükleme süresini önemli ölçüde hızlandırabilir.

**Hayır**

Önbelleğe alınmış proje verilerini kullanmayın. Projenin her yüklendiği her seferinde proje dosyalarını ayrıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ Programları Oluşturma](/cpp/build/projects-and-build-systems-cpp)
- [C/C++ Oluşturma Başvurusu](/cpp/build/reference/c-cpp-building-reference)