---
title: VC + + proje ayarları, projeler ve çözümler, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657858"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusu, [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] derleme günlüğü ve destekleyici dosya türleriyle ilgili proje ayarlarını tanımlamanıza olanak sağlar.

### <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Projeler ve çözümler**' i seçin ve ardından **VC + + proje ayarları**' nı seçin.

## <a name="build-customization-search-path"></a>Yapı özelleştirme arama yolu
 Projeleriniz için yapı kuralları tanımlamanıza yardımcı olan. Rules dosyalarını içeren dizinlerin listesini belirtir.

## <a name="build-logging"></a>Derleme günlüğü
 **Evet** Derleme günlüğü dosyasının oluşturulmasını etkinleştirir. Bu seçenek, projenin ara dosyalar dizininde bulunan BuildLog.htm oluşturur. Her yeni derleme önceki BuildLog.htm dosyanın üzerine yazar.

 **Hayır** Derleme günlüğü dosyasının oluşturulmasını devre dışı bırakır.

## <a name="build-timing"></a>Derleme zamanlaması
 **Evet** Derleme zamanlamasını etkinleştirir. Seçilirse, derleme işleminin tamamlaması için gereken süre çıkış penceresine gönderilir. Daha fazla bilgi için bkz. [Çıkış penceresi](../../ide/reference/output-window.md).

 **Hayır** Derleme zamanlamasını kapatır.

## <a name="extensions-to-hide"></a>Gizlenecek uzantılar
 **Tüm dosyaları göster** etkinleştirildiğinde **Çözüm Gezgini** görüntülenmeyen dosyaların dosya adı uzantılarını belirtir.

## <a name="extensions-to-include"></a>Dahil edilecek uzantılar
 Projenizde yer alan dosyaların dosya adı uzantılarını belirtir.

## <a name="maximum-concurrent-c-compilations"></a>Maksimum eşzamanlı C++ derlemeleri
 Paralel C++ derlemesi için kullanılacak en fazla CPU çekirdeği sayısını belirtir.

## <a name="show-environment-in-log"></a>Ortamı günlükte göster
 **Evet** Yapı günlük dosyasındaki ortam değişkenlerini listeler. Bu seçenek, proje derlemeleri sırasında tüm ortam değişkenlerini derleme günlüğü dosyasına yankılanması gerektiğini belirtir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] .

 **Hayır** Ortam değişkenlerini derleme günlük dosyasından hariç tutun.

## <a name="solution-explorer-mode"></a>Çözüm Gezgini modu
 **Yalnızca projedeki dosyaları göster** Yalnızca projedeki dosyaları göstermek için **Çözüm Gezgini** yapılandırır.

 **Tüm dosyaları göster** Proje klasöründeki dosyaları projede ve diskte göstermek için **Çözüm Gezgini** yapılandırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ programları oluşturma](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) [c/c++ oluşturma başvurusu](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
