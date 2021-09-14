---
description: Dia2dump örneği, bilgi için bir PDB dosyasını sorgulamak üzere Microsoft Debug Interface Access Software Development Kit'in (DIA SDK) nasıl kullanabileceğinizi gösterir.
title: Dia2dump Örnek | Microsoft Docs
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
ms.openlocfilehash: cdf5e84eaeace022d733d7f8521aecdbc2cd58d1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630645"
---
# <a name="dia2dump-sample"></a>Dia2dump Örneği

Dia2dump örneği, bilgi için bir PDB dosyasını sorgulamak üzere Microsoft Debug Interface Access Software Development Kit'in (DIA SDK) nasıl kullanabileceğinizi gösterir.

Dia2dump örneği, Visual Studio ve kaynak dosyalarını içerir. Derlenmiş yürütülebilir dosya komut satırdan çalışır. Bir program veritabanı (.pdb) dosyasının tamamının veya yalnızca ilgilendiğin bölümlerin içeriğini görüntüler.

## <a name="install-the-sample"></a>Örneği yükleme

Örnek, masaüstünde **C++** ile masaüstü geliştirme iş yükünü Visual Studio Yükleyicisi. Belirli iş yüklerini ve Visual Studio bileşenleri seçme hakkında bilgi için bkz. [Yükleme Visual Studio.](../../install/install-visual-studio.md)

Yüklendikten sonra örnek, \Visual Studio\Samples\DIA2Dump adlı bir DIA SDK alt dizinde yer alan yükleme dizinindedir.

## <a name="build-the-sample"></a>Örneği oluşturma

Varsayılan olarak, yükleme dizini korumalı bir dizindir. Bu, bu konumda örnek çözümü derlemek ve düzenlemek için Visual Studio geliştirici komut istemini veya örnek örneğini kullanmanız gerektiğini ifade eder. Derlemeyi basitleştirmek için, önce dosyaları örnek dizinden Belgeler klasörünüzdeki bir klasör gibi başka bir dizine kopyalamanızı ve ardından örneği derlemenizi öneririz.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Visual Studio'da Dia2Dump örneğini derlemek için

1. DIA2Dump.sln dosyasını Visual Studio. Çözümü başka bir dizine kopyalamadıysanız, yükseltilmiş izinlerle Visual Studio başlatmanız istenebilirsiniz.

1. Bu **Çözüm Gezgini** Dia2Dump projesini (çözümü değil) seçin.

1. Projenin Özellik Sayfaları **iletişim** kutusunu açın. Ayrıntılar için [bkz. Project Ile Çalışma.](/cpp/build/working-with-project-properties)

1. Yapılandırma **Özellikleri**  >  **C/C++ Genel**  >  **özellik** sayfasını açın.

1. Ek Dahil **Dizinleri özelliğinde** açılan liste denetimi ve ardından Düzenle'yi **seçin.**

1. Ek **Dahil Dizinleri iletişim** kutusunda, düzenleme alanına dizinini `$(VSInstallDir)DIA SDK\include` girin. Derleyicinin dia2.h dosyasını bulmalarını garanti etmek için bu dizini ekleyin. Değişikliklerinizi **kaydetmek** için Tamam'ı seçin.

1. Proje **özelliklerinde** yaptığınız değişiklikleri kaydetmek için Tamam'ı seçin.

1. Derleme menüsünde **Çözümü Yeniden** **Oluştur'a tıklayın.** Varsayılan olarak Visual Studio çözüm dizininin Bir Hata Ayıklama alt dizininde bulunan örneğin Hata ayıklama sürümünü derlemek için kullanılır.

1. Visual Studio’yu kapatın.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Komut satırına Dia2Dump örneğini derlemek için

1. Geliştirici komut istemi penceresinde, örnek dosyaları kopyalanan dizine geçin. Örneği başka bir dizine kopyalamadıysanız yükseltilmiş (yönetici olarak çalıştır) Geliştirici komut istemi penceresi kullansanız iyi olur.

1. Varsayılan Hata `nmake makefile` Ayıklama yapılandırmasını derlemek için komutunu dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Dia2Dump örneğini çalıştırma

Dia2Dump.exe hizmetleri sağlamak için *msdia*.dll COM sunucusuna bağlı olarak kullanılır. 2015 Visual Studio sürümünden itibaren sürüm msdia140.dll. COM *sunucusunun* msdia.dll başlatılmamışsa, çalışamadan önce msdia dia2dump.exe kaydetmelisiniz. DIA SDK dizininde DLL'nin x86 sürümünü içeren bir bin alt dizini vardır. x64 mimari makinelerinin sürümü bin\amd64, ARM sürümü ise bin\arm dizinindedir. Dll'i kaydetmek için yükseltilmiş bir Geliştirici komut istemi penceresi açın ve makine mimarinizin sürümünü içeren dizine geçin. COM sunucusunu `regsvr32 msdia140.dll` kaydetmek için komutunu girin.

### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Bir komut istemi açın ve kendi dia2dump.exe dizinine yazın.

1. Dosya adının `dia2dump filename` *incelenecek* PDB dosyasının adı olduğu komutu girin. PDB dosyası başka bir dizinde ise dosya adı olarak dosyanın tam *yolunu kullanın.* Bu komut PDB dosyasındaki tüm verileri listeler.

1. Dia2Dump'un yalnızca seçili bilgileri görüntülemek için başka seçenekleri vardır. Kullanılabilir `dia2dump -?` tüm seçenekleri listeleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Projelerini Taşıma, Geçirme ve Yükseltme](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
