---
title: C++ Proje Ayarları seçenekleri
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68918891"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu

Bu iletişim kutusu, günlük, performans ve destekleyici dosya türleri ile ilgili C++ yapı ve proje ayarlarını tanımlamanıza olanak tanır.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Projeler ve Çözümler'i**seçin ve ardından **VC++ Proje Ayarlarını**seçin.

## <a name="build-logging"></a>Yapı Günlüğü

 **Evet**

  Yapı günlüğü dosyasının oluşturulmasını açar. Bu seçenek, projenin ara dosya dizininde bulunan BuildLog.htm oluşturur. Her yeni yapı önceki BuildLog.htm dosyasının üzerine yazar.

 **Hayır**

  Yapı günlüğü dosyasının oluşturmasını kapatır.

## <a name="show-environment-in-log"></a>Günlükte Ortamı Göster

 **Evet**

Yapı günlüğü dosyasındaki ortam değişkenlerini listeler. Bu seçenek, C++ projelerinin oluşturulması sırasında tüm ortam değişkenlerini yapı günlüğü dosyasına yansıtacak şekilde belirtir.

 **Hayır**

Yapı günlüğü dosyasından ortam değişkenlerini hariç tut.

## <a name="build-timing"></a>Zamanlama Oluşturma

 **Evet**

  Yapı zamanlamasına döner. Seçilirse, yapının tamamlanması için gereken süre Çıktı penceresine nakledilir. Daha fazla bilgi için [Çıktı Penceresi'ne](../../ide/reference/output-window.md)bakın.

 **Hayır**

Yapı zamanlamasını kapatır.

## <a name="maximum-concurrent-c-compilations"></a>Maksimum eşzamanlı C++ derlemeleri

Paralel C++ derlemesi için kullanılacak maksimum CPU çekirdeği sayısını belirtir.

## <a name="extensions-to-include"></a>İçerecek Uzantılar

Projenize taşınabilir dosyaların dosya adı uzantılarını belirtir.

## <a name="extensions-to-hide"></a>Saklanacak Uzantılar

**Tüm Dosyaları Göster** etkinleştirildiğinde Çözüm **Gezgini'nde** görüntülenmeyen dosyaların dosya adı uzantılarını belirtir.

## <a name="build-customization-search-path"></a>Özelleştirme Arama Yolu Oluştur

Projeleriniz için yapı kurallarını tanımlamanıza yardımcı olan .rules dosyalarını içeren dizinler listesini belirtir.

## <a name="solution-explorer-mode"></a>Çözüm Explorer Modu

**Yalnızca projedeki dosyaları göster**

Çözüm **Gezgini'ni** yalnızca projedeki dosyaları görüntülemek için yapılandırır.

**Tüm dosyaları göster**

**Projedeki** dosyaları ve proje klasöründeki diskteki dosyaları göstermek için Solution Explorer'ı yapılandırır.

## <a name="enable-project-caching"></a>Proje Önbelleğe Alma etkinleştirme

**Evet**

Visual Studio'nun proje verilerini önbelleğe almalarını sağlar, böylece projeyi bir dahaki sefere açtığınızda önbelleğe alınmış verileri proje dosyalarından yeniden hesaplamak yerine yükleyebilir. Önbelleğe alınan verilerin kullanılması, proje yükleme süresini önemli ölçüde hızlandırabilir.

**Hayır**

Önbelleğe alınmış proje verilerini kullanmayın. Proje her yükyüklerinde proje dosyalarını ayrıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ Programları Oluşturma](/cpp/build/projects-and-build-systems-cpp)
- [C/C++ Oluşturma Başvurusu](/cpp/build/reference/c-cpp-building-reference)