## 検証環境

- macOS High Sierra (OSX 10.13.4)

```
$ sw_vers 
ProductName:	Mac OS X
ProductVersion:	10.13.4
BuildVersion:	17E199
```

## `libmecab.dylib` の場所

- `/usr/lib/libmecab.dylib`
- `libmecab.dylib` は `libmecab.1.0.0.dylib` のシンボリック・リンクである
- 同階層に `libmecabra.dylib` もある。（違いは不明）

```
$ ls -la /usr/lib | grep mecab
-rwxr-xr-x    1 root  wheel   1698592  3 28 13:03 libmecab.1.0.0.dylib
lrwxr-xr-x    1 root  wheel        20  2  1 08:15 libmecab.dylib -> libmecab.1.0.0.dylib
-rwxr-xr-x    1 root  wheel   5108304  3 28 13:02 libmecabra.dylib
```

## `libmecab.dylib`ライブラリの本体パス

以下は `otool -D /usr/lib/libmecab.dylib` の結果です。

```
$ otool -D /usr/lib/libmecab.dylib
/usr/lib/libmecab.dylib:
/usr/lib/libmecab.1.0.0.dylib
```

## `libmecab.dylib`ライブラリの依存関係

以下は `otool -L /usr/lib/libmecab.dylib` の結果です。

```
$ otool -L /usr/lib/libmecab.dylib
/usr/lib/libmecab.dylib:
	/usr/lib/libmecab.1.0.0.dylib (compatibility version 1.0.0, current version 779.7.5)
	/usr/lib/libicucore.A.dylib (compatibility version 1.0.0, current version 59.1.0)
	/usr/lib/libiconv.2.dylib (compatibility version 7.0.0, current version 7.0.0)
	/System/Library/Frameworks/CoreFoundation.framework/Versions/A/CoreFoundation (compatibility version 150.0.0, current version 1450.14.0)
	/usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 400.9.0)
	/usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1252.0.0)
```

## `libmecab.dylib`ライブラリがロードするコマンド

以下は `otool -l /usr/lib/libmecab.dylib` の結果です。


```
$ otool -l /usr/lib/libmecab.dylib
/usr/lib/libmecab.dylib:
Mach header
      magic cputype cpusubtype  caps    filetype ncmds sizeofcmds      flags
 0xfeedfacf 16777223          3  0x00           6    19       2064 0x02110085
Load command 0
      cmd LC_SEGMENT_64
  cmdsize 712
  segname __TEXT
   vmaddr 0x0000000000000000
   vmsize 0x00000000000b0000
  fileoff 0
 filesize 720896
  maxprot 0x00000007
 initprot 0x00000005
   nsects 8
    flags 0x0
Section
  sectname __text
   segname __TEXT
      addr 0x0000000000000d40
      size 0x0000000000043004
    offset 3392
     align 2^4 (16)
    reloff 0
    nreloc 0
     flags 0x80000400
 reserved1 0
 reserved2 0
Section
  sectname __stubs
   segname __TEXT
      addr 0x0000000000043d44
      size 0x0000000000000384
    offset 277828
     align 2^1 (2)
    reloff 0
    nreloc 0
     flags 0x80000408
 reserved1 0 (index into indirect symbol table)
 reserved2 6 (size of stubs)
Section
  sectname __stub_helper
   segname __TEXT
      addr 0x00000000000440c8
      size 0x00000000000005ba
    offset 278728
     align 2^2 (4)
    reloff 0
    nreloc 0
     flags 0x80000400
 reserved1 0
 reserved2 0
Section
  sectname __const
   segname __TEXT
      addr 0x0000000000044690
      size 0x0000000000060af2
    offset 280208
     align 2^4 (16)
    reloff 0
    nreloc 0
     flags 0x00000000
 reserved1 0
 reserved2 0
Section
  sectname __gcc_except_tab
   segname __TEXT
      addr 0x00000000000a5184
      size 0x00000000000069a0
    offset 676228
     align 2^2 (4)
    reloff 0
    nreloc 0
     flags 0x00000000
 reserved1 0
 reserved2 0
Section
  sectname __cstring
   segname __TEXT
      addr 0x00000000000abb24
      size 0x0000000000003753
    offset 703268
     align 2^0 (1)
    reloff 0
    nreloc 0
     flags 0x00000002
 reserved1 0
 reserved2 0
Section
  sectname __unwind_info
   segname __TEXT
      addr 0x00000000000af278
      size 0x0000000000000d50
    offset 717432
     align 2^2 (4)
    reloff 0
    nreloc 0
     flags 0x00000000
 reserved1 0
 reserved2 0
Section
  sectname __eh_frame
   segname __TEXT
      addr 0x00000000000affc8
      size 0x0000000000000038
    offset 720840
     align 2^3 (8)
    reloff 0
    nreloc 0
     flags 0x00000000
 reserved1 0
 reserved2 0
Load command 1
      cmd LC_SEGMENT_64
  cmdsize 632
  segname __DATA
   vmaddr 0x00000000000b0000
   vmsize 0x0000000000003000
  fileoff 720896
 filesize 12288
  maxprot 0x00000007
 initprot 0x00000003
   nsects 7
    flags 0x0
Section
  sectname __got
   segname __DATA
      addr 0x00000000000b0000
      size 0x00000000000000d8
    offset 720896
     align 2^3 (8)
    reloff 0
    nreloc 0
     flags 0x00000006
 reserved1 150 (index into indirect symbol table)
 reserved2 0
Section
  sectname __nl_symbol_ptr
   segname __DATA
      addr 0x00000000000b00d8
      size 0x0000000000000010
    offset 721112
     align 2^3 (8)
    reloff 0
    nreloc 0
     flags 0x00000006
 reserved1 177 (index into indirect symbol table)
 reserved2 0
Section
  sectname __la_symbol_ptr
   segname __DATA
      addr 0x00000000000b00e8
      size 0x00000000000004b0
    offset 721128
     align 2^3 (8)
    reloff 0
    nreloc 0
     flags 0x00000007
 reserved1 179 (index into indirect symbol table)
 reserved2 0
Section
  sectname __const
   segname __DATA
      addr 0x00000000000b05a0
      size 0x0000000000001578
    offset 722336
     align 2^4 (16)
    reloff 0
    nreloc 0
     flags 0x00000000
 reserved1 0
 reserved2 0
Section
  sectname __data
   segname __DATA
      addr 0x00000000000b1b20
      size 0x0000000000000800
    offset 727840
     align 2^4 (16)
    reloff 0
    nreloc 0
     flags 0x00000000
 reserved1 0
 reserved2 0
Section
  sectname __bss
   segname __DATA
      addr 0x00000000000b2320
      size 0x0000000000000220
    offset 0
     align 2^3 (8)
    reloff 0
    nreloc 0
     flags 0x00000001
 reserved1 0
 reserved2 0
Section
  sectname __common
   segname __DATA
      addr 0x00000000000b2540
      size 0x000000000000023c
    offset 0
     align 2^3 (8)
    reloff 0
    nreloc 0
     flags 0x00000001
 reserved1 0
 reserved2 0
Load command 2
      cmd LC_SEGMENT_64
  cmdsize 72
  segname __LINKEDIT
   vmaddr 0x00000000000b3000
   vmsize 0x000000000001b000
  fileoff 733184
 filesize 110048
  maxprot 0x00000007
 initprot 0x00000001
   nsects 0
    flags 0x0
Load command 3
          cmd LC_ID_DYLIB
      cmdsize 56
         name /usr/lib/libmecab.1.0.0.dylib (offset 24)
   time stamp 1 Thu Jan  1 09:00:01 1970
      current version 779.7.5
compatibility version 1.0.0
Load command 4
            cmd LC_DYLD_INFO_ONLY
        cmdsize 48
     rebase_off 733184
    rebase_size 400
       bind_off 733584
      bind_size 2520
  weak_bind_off 736104
 weak_bind_size 152
  lazy_bind_off 736256
 lazy_bind_size 5360
     export_off 741616
    export_size 672
Load command 5
     cmd LC_SYMTAB
 cmdsize 24
  symoff 744800
   nsyms 1196
  stroff 765252
 strsize 62208
Load command 6
            cmd LC_DYSYMTAB
        cmdsize 80
      ilocalsym 0
      nlocalsym 964
     iextdefsym 964
     nextdefsym 35
      iundefsym 999
      nundefsym 197
         tocoff 0
           ntoc 0
      modtaboff 0
        nmodtab 0
   extrefsymoff 0
    nextrefsyms 0
 indirectsymoff 763936
  nindirectsyms 329
      extreloff 0
        nextrel 0
      locreloff 0
        nlocrel 0
Load command 7
     cmd LC_UUID
 cmdsize 24
    uuid 334D4742-BDDD-3C2D-BBEB-85B32643BFA0
Load command 8
      cmd LC_VERSION_MIN_MACOSX
  cmdsize 16
  version 10.13
      sdk 10.13
Load command 9
      cmd LC_SOURCE_VERSION
  cmdsize 16
  version 779.7.6
Load command 10
      cmd LC_SEGMENT_SPLIT_INFO
  cmdsize 16
  dataoff 742288
 datasize 1600
Load command 11
          cmd LC_LOAD_DYLIB
      cmdsize 56
         name /usr/lib/libicucore.A.dylib (offset 24)
   time stamp 2 Thu Jan  1 09:00:02 1970
      current version 59.1.0
compatibility version 1.0.0
Load command 12
          cmd LC_LOAD_DYLIB
      cmdsize 56
         name /usr/lib/libiconv.2.dylib (offset 24)
   time stamp 2 Thu Jan  1 09:00:02 1970
      current version 7.0.0
compatibility version 7.0.0
Load command 13
          cmd LC_LOAD_DYLIB
      cmdsize 104
         name /System/Library/Frameworks/CoreFoundation.framework/Versions/A/CoreFoundation (offset 24)
   time stamp 2 Thu Jan  1 09:00:02 1970
      current version 1450.14.0
compatibility version 150.0.0
Load command 14
          cmd LC_LOAD_DYLIB
      cmdsize 48
         name /usr/lib/libc++.1.dylib (offset 24)
   time stamp 2 Thu Jan  1 09:00:02 1970
      current version 400.9.0
compatibility version 1.0.0
Load command 15
          cmd LC_LOAD_DYLIB
      cmdsize 56
         name /usr/lib/libSystem.B.dylib (offset 24)
   time stamp 2 Thu Jan  1 09:00:02 1970
      current version 1252.0.0
compatibility version 1.0.0
Load command 16
      cmd LC_FUNCTION_STARTS
  cmdsize 16
  dataoff 743888
 datasize 864
Load command 17
      cmd LC_DATA_IN_CODE
  cmdsize 16
  dataoff 744752
 datasize 48
Load command 18
      cmd LC_CODE_SIGNATURE
  cmdsize 16
  dataoff 827472
 datasize 15760
```

## 参考文献

- [dynamic library の OS Xの補足](https://qiita.com/false-git@github/items/cb4528701752f76cfaa7) @ Qiita
- [macOSのコマンドラインアプリでdylibをよろしく扱う方法](https://qiita.com/omochimetaru/items/21d662b8df8bce1bc5ca) @ Qiita

