---
title: Kaynak denetim bilgilerini .proj ve .sln dosyalarından kaldırma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705585"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj ve .Sln Dosyalarından Kaynak Denetimi Bilgilerinin Kaldırılması
Kaynak Denetimi Eklentisi API'sinin sürüm 1.2'sinde SCC bilgileri bir MSSCCPRJ'de depolanır. SCC dosyası. MSSCCPRJ avantajı. SCC dosyası, SCC bilgilerinin .proj ve .sln dosyalarında olduğu gibi kaynak denetiminde olmamasıdır.

## <a name="version-12-changes"></a>Sürüm 1.2 Değişiklikler
 Kaynak Denetimi Eklentisi API sürüm 1.1'i temel alan kaynak denetimi eklentilerinde, kaynak denetimi hakkındaki bilgiler proje (.proj) ve solution (.sln) dosyalarında depolanır. Kaynak denetim bilgilerinin veritabanı konumu AuxPath tarafından belirtilir ve veritabanı içindeki belirli konum ProjName tarafından belirtilir. ProjName genellikle bu işlemlerden sonra geçersiz olacağından, bu davranış dal, çatal veya kopyalama işlemlerinden sonra sorunlara neden olabilir.

 Kaynak Denetimi Eklentisi API sürüm 1.1'de, IDE bir eklentinin MSSCCPRJ'yi destekletip desteklemedigini algılamak için ~SAK dosyalarını kullandi. Kaynak kontrol bilgilerini depolamak için SCC yöntemi. Kaynak Denetimi Eklentisi API sürüm 1.2, MSSCCPRJ desteğini algılamak için yeni bir yetenek sağlar. Bir ~ SAK dosyası kullanmadan SCC dosyası. Daha fazla bilgi için [~ SAK Dosyalarıelime](../../extensibility/internals/elimination-of-tilde-sak-files.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
