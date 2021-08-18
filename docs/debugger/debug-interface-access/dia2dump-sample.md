---
description: Dia2dump örnek, Microsoft hata ayıklama arabirimi erişim yazılım geliştirme seti 'nin (DIA SDK) bilgi için bir PDB dosyasını sorgulamak için nasıl kullanılacağını gösterir.
title: Dia2dump örneği | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 796ad78bfe8337db7bf177235284624877a7ed555da025fff8728b9cc2ce8b6b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345495"
---
# <a name="dia2dump-sample"></a>Dia2dump Örneği

Dia2dump örnek, Microsoft hata ayıklama arabirimi erişim yazılım geliştirme seti 'nin (DIA SDK) bilgi için bir PDB dosyasını sorgulamak için nasıl kullanılacağını gösterir.

Dia2dump örneği Visual Studio ile yüklenir ve çözümü ve kaynak dosyalarını içerir. Derlenmiş yürütülebilir dosya komut satırından çalışır. Tüm program veritabanı (. pdb) dosyasının veya ilgilendiğiniz bölümlerin içeriğini gösterebilir.

## <a name="install-the-sample"></a>Örneği yükler

örnek, Visual Studio Yükleyicisi C++ iş yüküne **sahip masaüstü geliştirmeyi** seçtiğinizde yüklenir. Visual Studio yüklemek ve belirli iş yüklerini ve bireysel bileşenleri seçmek hakkında bilgi için bkz. [install Visual Studio](../../install/install-visual-studio.md).

yüklendiğinde, örnek, \dia sdk\samples\dia2dumpadlı bir alt dizinde Visual Studio yükleme dizininizde bulunur.

## <a name="build-the-sample"></a>Örneği oluşturma

Varsayılan olarak, yükleme dizini korumalı bir dizindir. yani, bu konumda örnek çözümü derlemek ve düzenlemek için yükseltilmiş bir geliştirici komut istemi veya Visual Studio örneğini kullanmanız gerekir. Derlemeyi basitleştirmek için, önce dosyaları örnek dizinden belgeler klasörünüzdeki bir klasör gibi başka bir dizine kopyalamanız ve sonra örneği oluşturmanız önerilir.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Visual Studio içinde Dia2Dump örneğini oluşturmak için

1. Visual Studio içinde DIA2Dump. sln dosyasını açın. çözümü başka bir dizine kopyalamadıysanız, Visual Studio yükseltilmiş izinlerle yeniden başlatmanız istenebilir.

1. **Çözüm Gezgini**, Dia2Dump projesini seçin (çözümü değil).

1. Projenin **Özellik sayfaları** iletişim kutusunu açın. ayrıntılar için bkz. [Project özellikleriyle çalışma](/cpp/build/working-with-project-properties).

1. **Yapılandırma özellikleri**  >  **C/C++**  >  **genel** özellik sayfasını açın.

1. **Ek Içerme dizinleri** özelliğinde, açılan denetimi seçin ve ardından **Düzenle**' yi seçin.

1. **Ek Içerik dizinleri** iletişim kutusunda, Düzenle alanına, `$(VSInstallDir)DIA SDK\include` dizini girin. Derleyicinin dia2. h dosyasını bulabileceği garantilemek için bu dizini ekleyin. Değişikliklerinizi kaydetmek için **Tamam ' ı** seçin.

1. Değişikliklerinizi proje özelliklerine kaydetmek için **Tamam ' ı** seçin.

1. **Derle** menüsünde **çözümü yeniden derle**' yi seçin. varsayılan olarak Visual Studio, çözüm dizininin bir hata ayıklama alt dizininde bulunan örneğin bir hata ayıklama sürümü oluşturur.

1. Visual Studio’yu kapatın.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Komut satırında Dia2Dump örneğini oluşturmak için

1. Geliştirici komut istemi penceresinde, örnek dosyaları kopyaladığınız dizine geçin. Örneği başka bir dizine kopyalamadıysanız yükseltilmiş (yönetici olarak çalıştır) Geliştirici komut istemi penceresi kullanmanız gerekir.

1. `nmake makefile`dia2dump.exe varsayılan hata ayıklama yapılandırmasını derlemek için komutunu girin.

## <a name="run-the-dia2dump-sample"></a>Dia2Dump örneğini çalıştırma

Dia2Dump.exe, hizmetlerini sağlamak için MSDIA *sürümüne*.dll com sunucusuna bağımlıdır. Visual Studio 2015 ' den başlayarak sürüm msdia140.dll. MSDIA *sürümü*.dll com sunucusu başlatılmazsa, dia2dump.exe çalışmadan önce kaydolmanız gerekir. DIA SDK dizininde DLL 'nin x86 sürümünü içeren bir bin alt dizini vardır. X64 mimari makineler için bir sürüm, bin\amd64 ' te ve ARM için bir sürüm de bin\arm. Dll 'yi kaydetmek için, yükseltilmiş bir geliştirici komut istemi penceresi açın ve makine mimarinizin sürümünü içeren dizine geçin. `regsvr32 msdia140.dll`Com sunucusunu kaydetmek için komutunu girin.

### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Bir komut istemi açın ve derlediniz dia2dump.exe içeren dizine geçin.

1. `dia2dump filename` *Dosya adının* , incelenecek bir pdb dosyasının adı olduğu komutu girin. PDB dosyası başka bir dizinse dosya *adı* olarak dosyanın tam yolunu kullanın. Bu komut PDB dosyasındaki tüm verileri listeler.

1. Dia2Dump yalnızca seçilen bilgileri görüntülemeye yönelik başka seçeneklere sahiptir. `dia2dump -?`Tüm kullanılabilir seçenekleri listelemek için komutunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
