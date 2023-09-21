# XXml

## Annotation
Simple and universal library for large XML files parsing with acceptable speed, supports:
- Unity >= 18
- .NET Framework 4.8
- .NET Core 3.2
- .NET 5
- .NET 6

## Benchmarks
```
BenchmarkDotNet v0.13.8, Windows 10 (10.0.19045.3324/22H2/2022Update)
11th Gen Intel Core i5-11400 2.60GHz, 1 CPU, 12 logical and 6 physical cores
.NET SDK 6.0.407
  [Host]    : .NET 6.0.21 (6.0.2123.36311), X64 RyuJIT AVX2 DEBUG
  RyuJitX64 : .NET 6.0.21 (6.0.2123.36311), X64 RyuJIT AVX2

Job=RyuJitX64  Jit=RyuJit  Platform=X64  
```
<details>
  <summary>150 mb file size (100000 items)</summary>

| Method               | Mean     | Error   | StdDev   | Ratio | RatioSD | Gen0      | Allocated native memory | Native memory leak | Allocated   | Alloc Ratio |
|--------------------- |---------:|--------:|---------:|------:|--------:|----------:|------------------------:|-------------------:|------------:|------------:|
| XXml                 | 382.2 ms | 7.31 ms | 18.87 ms |  1.00 |    0.00 |         - |              507,294 KB |                  - |     1.02 KB |        1.00 |
| System.Xml.XmlReader | 421.6 ms | 6.24 ms |  5.83 ms |  1.10 |    0.05 | 4000.0000 |                    0 KB |                  - | 29161.63 KB |   28,493.81 |

</details>

<details>
  <summary>800 mb file size (500000 items)</summary>
  
| Method               | Mean     | Error   | StdDev   | Ratio | RatioSD | Gen0      | Allocated native memory | Native memory leak | Allocated  | Alloc Ratio |
|--------------------- |---------:|--------:|---------:|------:|--------:|----------:|------------------------:|-------------------:|-----------:|------------:|
| XXml                 | 404.4 ms | 8.79 ms | 25.37 ms |  1.00 |    0.00 |         - |              507,294 KB |                  - |    1.02 KB |        1.00 |
| System.Xml.XmlReader | 433.6 ms | 8.62 ms | 12.91 ms |  1.08 |    0.08 | 4000.0000 |                    0 KB |                  - | 29149.8 KB |   28,482.25 |

</details>

<details>
  <summary>1580 mb file size (1000000 items)</summary>
  
| Method               | Mean     | Error   | StdDev   | Ratio | RatioSD | Gen0      | Allocated native memory | Native memory leak | Allocated  | Alloc Ratio |
|--------------------- |---------:|--------:|---------:|------:|--------:|----------:|------------------------:|-------------------:|-----------:|------------:|
| XXml                 | 384.9 ms | 7.69 ms | 15.70 ms |  1.00 |    0.00 |         - |              507,294 KB |                  - |    1.02 KB |        1.00 |
| System.Xml.XmlReader | 424.1 ms | 8.39 ms |  7.85 ms |  1.10 |    0.04 | 4000.0000 |                    0 KB |                  - | 29149.8 KB |   28,482.25 |

</details>

<details>
  <summary>2150 mb file size (2000000 items)</summary>
  
| Method               | Mean     | Error   | StdDev   | Ratio | RatioSD | Gen0      | Allocated native memory | Native memory leak | Allocated   | Alloc Ratio |
|--------------------- |---------:|--------:|---------:|------:|--------:|----------:|------------------------:|-------------------:|------------:|------------:|
| XXml                 | 389.2 ms | 7.71 ms | 20.19 ms |  1.00 |    0.00 |         - |              507,294 KB |                  - |     1.02 KB |        1.00 |
| System.Xml.XmlReader | 428.4 ms | 8.43 ms | 12.87 ms |  1.09 |    0.07 | 4000.0000 |                    0 KB |                  - | 29150.01 KB |   28,482.45 |

</details>

## Usage

```csharp
# Get XML from file
var xml = XmlParser.ParseFile(FilePath);

# Get all nodes by type
xml.GetAllNodes(XmlNodeType.ElementNode)
```
