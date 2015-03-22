=========
Handbrake
=========

I use Handbrake to convert my videos into :doc:`MP4 (M4V) format <../../formats/video>`.

Lip Sync Issues
===============

I discovered after the first round of scanning movies that there were issues with graininess, cropping, and lip sync on some movies. I rescanned them. After rescan, these still had some issues:

- Buffy the Vampire Slayer (1992) - Possible naturally bad sync. Everything is off by just a couple of frames.
- Christmas Vacation (1989) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- Elf (2003) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- Eraser (1996) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- GI Jane (1997) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- Iron Monkey (1993) - Almost looks like the wrong language, but this is apparently normal for some Cantonese films - they overdub themselves.
- It's a Very Merry Muppet Christmas Movie (2002) - Possible naturally bad sync. Everything is just a little off.
- Jay and Silent Bob Strike Back (2001) - This is a variable frame rate movie and it seems to have naturally bad sync. Switching to constant frame rate makes some of the sections stutter.
- Labyrinth (1986) - Possible naturally bad sync.
- Lethal Weapon (the entire series) - All of these seem to have naturally bad sync.
- Maverick (1994) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.

I stopped tracking the complete list. It kind of sucks, but it is what it is.

Part of the way I fixed this was to start using **constant frame rate** in all my conversions rather than variable frame rate. I noticed that, as a general rule, this reduced or removed many of the lip sync problems I saw.

User Presets
============

The following is my set of presets. If you put these in ``%AppData%\Roaming\Handbrake\user_presets.xml`` then you'll see the same settings as me.

.. sourcecode:: xml

    <?xml version="1.0"?>
    <ArrayOfPreset xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Preset>
        <Category>User Presets</Category>
        <Description />
        <IsBuildIn>false</IsBuildIn>
        <IsDefault>false</IsDefault>
        <Name>Illig High Profile - SD Film</Name>
        <PictureSettingsMode>Custom</PictureSettingsMode>
        <UseDeinterlace>false</UseDeinterlace>
        <Task>
          <Title>0</Title>
          <Angle>0</Angle>
          <PointToPointMode>Chapters</PointToPointMode>
          <StartPoint>0</StartPoint>
          <EndPoint>0</EndPoint>
          <OutputFormat>Mp4</OutputFormat>
          <OptimizeMP4>false</OptimizeMP4>
          <IPod5GSupport>false</IPod5GSupport>
          <Width xsi:nil="true" />
          <Height xsi:nil="true" />
          <MaxWidth xsi:nil="true" />
          <MaxHeight xsi:nil="true" />
          <Cropping>
            <Top>0</Top>
            <Bottom>0</Bottom>
            <Left>0</Left>
            <Right>0</Right>
          </Cropping>
          <HasCropping>false</HasCropping>
          <Anamorphic>Loose</Anamorphic>
          <DisplayWidth xsi:nil="true" />
          <KeepDisplayAspect>false</KeepDisplayAspect>
          <PixelAspectX>0</PixelAspectX>
          <PixelAspectY>0</PixelAspectY>
          <Modulus>2</Modulus>
          <Deinterlace>Off</Deinterlace>
          <Decomb>Default</Decomb>
          <Detelecine>Off</Detelecine>
          <Denoise>Off</Denoise>
          <DenoisePreset>Weak</DenoisePreset>
          <DenoiseTune>None</DenoiseTune>
          <Deblock>0</Deblock>
          <Grayscale>false</Grayscale>
          <VideoEncodeRateType>ConstantQuality</VideoEncodeRateType>
          <VideoEncoder>X264</VideoEncoder>
          <FramerateMode>CFR</FramerateMode>
          <Quality>18</Quality>
          <VideoBitrate xsi:nil="true" />
          <TwoPass>false</TwoPass>
          <TurboFirstPass>false</TurboFirstPass>
          <Framerate xsi:nil="true" />
          <AudioTracks>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>fdkaac</Encoder>
              <Gain>0</Gain>
              <MixDown>DolbyProLogicII</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>Ac3Passthrough</Encoder>
              <Gain>0</Gain>
              <MixDown>Auto</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
          </AudioTracks>
          <AllowedPassthruOptions>
            <AudioAllowAACPass>true</AudioAllowAACPass>
            <AudioAllowAC3Pass>true</AudioAllowAC3Pass>
            <AudioAllowDTSHDPass>true</AudioAllowDTSHDPass>
            <AudioAllowDTSPass>true</AudioAllowDTSPass>
            <AudioAllowMP3Pass>true</AudioAllowMP3Pass>
            <AudioEncoderFallback>Ac3</AudioEncoderFallback>
          </AllowedPassthruOptions>
          <SubtitleTracks />
          <IncludeChapterMarkers>true</IncludeChapterMarkers>
          <ChapterNames />
          <X264Preset>Slower</X264Preset>
          <QsvPreset>Quality</QsvPreset>
          <H264Profile>High</H264Profile>
          <H264Level>4.1</H264Level>
          <X264Tune>Film</X264Tune>
          <FastDecode>false</FastDecode>
          <X265Preset>VeryFast</X265Preset>
          <H265Profile>Main</H265Profile>
          <X265Tune>None</X265Tune>
          <PreviewStartAt xsi:nil="true" />
          <PreviewDuration xsi:nil="true" />
          <IsPreviewEncode>false</IsPreviewEncode>
          <PreviewEncodeDuration>0</PreviewEncodeDuration>
          <ShowAdvancedTab>false</ShowAdvancedTab>
        </Task>
        <UsePictureFilters>true</UsePictureFilters>
      </Preset>
      <Preset>
        <Category>User Presets</Category>
        <Description />
        <IsBuildIn>false</IsBuildIn>
        <IsDefault>false</IsDefault>
        <Name>Illig High Profile - SD 2D Anim</Name>
        <PictureSettingsMode>Custom</PictureSettingsMode>
        <UseDeinterlace>false</UseDeinterlace>
        <Task>
          <Title>0</Title>
          <Angle>0</Angle>
          <PointToPointMode>Chapters</PointToPointMode>
          <StartPoint>0</StartPoint>
          <EndPoint>0</EndPoint>
          <OutputFormat>Mp4</OutputFormat>
          <OptimizeMP4>false</OptimizeMP4>
          <IPod5GSupport>false</IPod5GSupport>
          <Width xsi:nil="true" />
          <Height xsi:nil="true" />
          <MaxWidth xsi:nil="true" />
          <MaxHeight xsi:nil="true" />
          <Cropping>
            <Top>0</Top>
            <Bottom>0</Bottom>
            <Left>0</Left>
            <Right>0</Right>
          </Cropping>
          <HasCropping>false</HasCropping>
          <Anamorphic>Loose</Anamorphic>
          <DisplayWidth xsi:nil="true" />
          <KeepDisplayAspect>false</KeepDisplayAspect>
          <PixelAspectX>0</PixelAspectX>
          <PixelAspectY>0</PixelAspectY>
          <Modulus>2</Modulus>
          <Deinterlace>Off</Deinterlace>
          <Decomb>Default</Decomb>
          <Detelecine>Off</Detelecine>
          <Denoise>Off</Denoise>
          <DenoisePreset>Weak</DenoisePreset>
          <DenoiseTune>None</DenoiseTune>
          <Deblock>0</Deblock>
          <Grayscale>false</Grayscale>
          <VideoEncodeRateType>ConstantQuality</VideoEncodeRateType>
          <VideoEncoder>X264</VideoEncoder>
          <FramerateMode>CFR</FramerateMode>
          <Quality>18</Quality>
          <VideoBitrate xsi:nil="true" />
          <TwoPass>false</TwoPass>
          <TurboFirstPass>false</TurboFirstPass>
          <Framerate xsi:nil="true" />
          <AudioTracks>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>fdkaac</Encoder>
              <Gain>0</Gain>
              <MixDown>DolbyProLogicII</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>Ac3Passthrough</Encoder>
              <Gain>0</Gain>
              <MixDown>Auto</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
          </AudioTracks>
          <AllowedPassthruOptions>
            <AudioAllowAACPass>true</AudioAllowAACPass>
            <AudioAllowAC3Pass>true</AudioAllowAC3Pass>
            <AudioAllowDTSHDPass>true</AudioAllowDTSHDPass>
            <AudioAllowDTSPass>true</AudioAllowDTSPass>
            <AudioAllowMP3Pass>true</AudioAllowMP3Pass>
            <AudioEncoderFallback>Ac3</AudioEncoderFallback>
          </AllowedPassthruOptions>
          <SubtitleTracks />
          <IncludeChapterMarkers>true</IncludeChapterMarkers>
          <ChapterNames />
          <X264Preset>Slower</X264Preset>
          <QsvPreset>Quality</QsvPreset>
          <H264Profile>High</H264Profile>
          <H264Level>4.1</H264Level>
          <X264Tune>Animation</X264Tune>
          <FastDecode>false</FastDecode>
          <X265Preset>VeryFast</X265Preset>
          <H265Profile>Main</H265Profile>
          <X265Tune>None</X265Tune>
          <PreviewStartAt xsi:nil="true" />
          <PreviewDuration xsi:nil="true" />
          <IsPreviewEncode>false</IsPreviewEncode>
          <PreviewEncodeDuration>0</PreviewEncodeDuration>
          <ShowAdvancedTab>false</ShowAdvancedTab>
        </Task>
        <UsePictureFilters>true</UsePictureFilters>
      </Preset>
      <Preset>
        <Category>User Presets</Category>
        <Description />
        <IsBuildIn>false</IsBuildIn>
        <IsDefault>false</IsDefault>
        <Name>Illig High Profile - SD Grain</Name>
        <PictureSettingsMode>Custom</PictureSettingsMode>
        <UseDeinterlace>false</UseDeinterlace>
        <Task>
          <Title>0</Title>
          <Angle>0</Angle>
          <PointToPointMode>Chapters</PointToPointMode>
          <StartPoint>0</StartPoint>
          <EndPoint>0</EndPoint>
          <OutputFormat>Mp4</OutputFormat>
          <OptimizeMP4>false</OptimizeMP4>
          <IPod5GSupport>false</IPod5GSupport>
          <Width xsi:nil="true" />
          <Height xsi:nil="true" />
          <MaxWidth xsi:nil="true" />
          <MaxHeight xsi:nil="true" />
          <Cropping>
            <Top>0</Top>
            <Bottom>0</Bottom>
            <Left>0</Left>
            <Right>0</Right>
          </Cropping>
          <HasCropping>false</HasCropping>
          <Anamorphic>Loose</Anamorphic>
          <DisplayWidth xsi:nil="true" />
          <KeepDisplayAspect>false</KeepDisplayAspect>
          <PixelAspectX>0</PixelAspectX>
          <PixelAspectY>0</PixelAspectY>
          <Modulus>2</Modulus>
          <Deinterlace>Off</Deinterlace>
          <Decomb>Default</Decomb>
          <Detelecine>Off</Detelecine>
          <Denoise>Off</Denoise>
          <DenoisePreset>Weak</DenoisePreset>
          <DenoiseTune>None</DenoiseTune>
          <Deblock>0</Deblock>
          <Grayscale>false</Grayscale>
          <VideoEncodeRateType>ConstantQuality</VideoEncodeRateType>
          <VideoEncoder>X264</VideoEncoder>
          <FramerateMode>CFR</FramerateMode>
          <Quality>18</Quality>
          <VideoBitrate xsi:nil="true" />
          <TwoPass>false</TwoPass>
          <TurboFirstPass>false</TurboFirstPass>
          <Framerate xsi:nil="true" />
          <AudioTracks>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>fdkaac</Encoder>
              <Gain>0</Gain>
              <MixDown>DolbyProLogicII</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>Ac3Passthrough</Encoder>
              <Gain>0</Gain>
              <MixDown>Auto</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
          </AudioTracks>
          <AllowedPassthruOptions>
            <AudioAllowAACPass>true</AudioAllowAACPass>
            <AudioAllowAC3Pass>true</AudioAllowAC3Pass>
            <AudioAllowDTSHDPass>true</AudioAllowDTSHDPass>
            <AudioAllowDTSPass>true</AudioAllowDTSPass>
            <AudioAllowMP3Pass>true</AudioAllowMP3Pass>
            <AudioEncoderFallback>Ac3</AudioEncoderFallback>
          </AllowedPassthruOptions>
          <SubtitleTracks />
          <IncludeChapterMarkers>true</IncludeChapterMarkers>
          <ChapterNames />
          <X264Preset>Slower</X264Preset>
          <QsvPreset>Quality</QsvPreset>
          <H264Profile>High</H264Profile>
          <H264Level>4.1</H264Level>
          <X264Tune>Grain</X264Tune>
          <FastDecode>false</FastDecode>
          <X265Preset>VeryFast</X265Preset>
          <H265Profile>Main</H265Profile>
          <X265Tune>None</X265Tune>
          <PreviewStartAt xsi:nil="true" />
          <PreviewDuration xsi:nil="true" />
          <IsPreviewEncode>false</IsPreviewEncode>
          <PreviewEncodeDuration>0</PreviewEncodeDuration>
          <ShowAdvancedTab>false</ShowAdvancedTab>
        </Task>
        <UsePictureFilters>true</UsePictureFilters>
      </Preset>
      <Preset>
        <Category>User Presets</Category>
        <IsBuildIn>false</IsBuildIn>
        <IsDefault>false</IsDefault>
        <Name>Illig High Profile - HD Film</Name>
        <PictureSettingsMode>Custom</PictureSettingsMode>
        <UseDeinterlace>false</UseDeinterlace>
        <Task>
          <Title>0</Title>
          <Angle>0</Angle>
          <PointToPointMode>Chapters</PointToPointMode>
          <StartPoint>0</StartPoint>
          <EndPoint>0</EndPoint>
          <OutputFormat>Mp4</OutputFormat>
          <OptimizeMP4>false</OptimizeMP4>
          <IPod5GSupport>false</IPod5GSupport>
          <Width xsi:nil="true" />
          <Height xsi:nil="true" />
          <MaxWidth xsi:nil="true" />
          <MaxHeight xsi:nil="true" />
          <Cropping>
            <Top>0</Top>
            <Bottom>0</Bottom>
            <Left>0</Left>
            <Right>0</Right>
          </Cropping>
          <HasCropping>false</HasCropping>
          <Anamorphic>Loose</Anamorphic>
          <DisplayWidth xsi:nil="true" />
          <KeepDisplayAspect>false</KeepDisplayAspect>
          <PixelAspectX>0</PixelAspectX>
          <PixelAspectY>0</PixelAspectY>
          <Modulus>2</Modulus>
          <Deinterlace>Off</Deinterlace>
          <Decomb>Off</Decomb>
          <Detelecine>Off</Detelecine>
          <Denoise>Off</Denoise>
          <DenoisePreset>Weak</DenoisePreset>
          <DenoiseTune>None</DenoiseTune>
          <Deblock>4</Deblock>
          <Grayscale>false</Grayscale>
          <VideoEncodeRateType>ConstantQuality</VideoEncodeRateType>
          <VideoEncoder>X264</VideoEncoder>
          <FramerateMode>VFR</FramerateMode>
          <Quality>21</Quality>
          <VideoBitrate xsi:nil="true" />
          <TwoPass>false</TwoPass>
          <TurboFirstPass>false</TurboFirstPass>
          <Framerate xsi:nil="true" />
          <AudioTracks>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>fdkaac</Encoder>
              <Gain>0</Gain>
              <MixDown>DolbyProLogicII</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>Ac3Passthrough</Encoder>
              <Gain>0</Gain>
              <MixDown>Auto</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
          </AudioTracks>
          <AllowedPassthruOptions>
            <AudioAllowAACPass>true</AudioAllowAACPass>
            <AudioAllowAC3Pass>true</AudioAllowAC3Pass>
            <AudioAllowDTSHDPass>true</AudioAllowDTSHDPass>
            <AudioAllowDTSPass>true</AudioAllowDTSPass>
            <AudioAllowMP3Pass>true</AudioAllowMP3Pass>
            <AudioEncoderFallback>Ac3</AudioEncoderFallback>
          </AllowedPassthruOptions>
          <SubtitleTracks />
          <IncludeChapterMarkers>true</IncludeChapterMarkers>
          <ChapterNames />
          <X264Preset>Slower</X264Preset>
          <QsvPreset>Quality</QsvPreset>
          <H264Profile>High</H264Profile>
          <H264Level>4.1</H264Level>
          <X264Tune>Film</X264Tune>
          <FastDecode>false</FastDecode>
          <X265Preset>VeryFast</X265Preset>
          <H265Profile>Main</H265Profile>
          <X265Tune>None</X265Tune>
          <PreviewStartAt xsi:nil="true" />
          <PreviewDuration xsi:nil="true" />
          <IsPreviewEncode>false</IsPreviewEncode>
          <PreviewEncodeDuration>0</PreviewEncodeDuration>
          <ShowAdvancedTab>false</ShowAdvancedTab>
        </Task>
        <UsePictureFilters>true</UsePictureFilters>
      </Preset>
      <Preset>
        <Category>User Presets</Category>
        <IsBuildIn>false</IsBuildIn>
        <IsDefault>false</IsDefault>
        <Name>Illig High Profile - HD 2D Anim</Name>
        <PictureSettingsMode>Custom</PictureSettingsMode>
        <UseDeinterlace>false</UseDeinterlace>
        <Task>
          <Title>0</Title>
          <Angle>0</Angle>
          <PointToPointMode>Chapters</PointToPointMode>
          <StartPoint>0</StartPoint>
          <EndPoint>0</EndPoint>
          <OutputFormat>Mp4</OutputFormat>
          <OptimizeMP4>false</OptimizeMP4>
          <IPod5GSupport>false</IPod5GSupport>
          <Width xsi:nil="true" />
          <Height xsi:nil="true" />
          <MaxWidth xsi:nil="true" />
          <MaxHeight xsi:nil="true" />
          <Cropping>
            <Top>0</Top>
            <Bottom>0</Bottom>
            <Left>0</Left>
            <Right>0</Right>
          </Cropping>
          <HasCropping>false</HasCropping>
          <Anamorphic>Loose</Anamorphic>
          <DisplayWidth xsi:nil="true" />
          <KeepDisplayAspect>false</KeepDisplayAspect>
          <PixelAspectX>0</PixelAspectX>
          <PixelAspectY>0</PixelAspectY>
          <Modulus>2</Modulus>
          <Deinterlace>Off</Deinterlace>
          <Decomb>Off</Decomb>
          <Detelecine>Off</Detelecine>
          <Denoise>Off</Denoise>
          <DenoisePreset>Weak</DenoisePreset>
          <DenoiseTune>None</DenoiseTune>
          <Deblock>4</Deblock>
          <Grayscale>false</Grayscale>
          <VideoEncodeRateType>ConstantQuality</VideoEncodeRateType>
          <VideoEncoder>X264</VideoEncoder>
          <FramerateMode>VFR</FramerateMode>
          <Quality>21</Quality>
          <VideoBitrate xsi:nil="true" />
          <TwoPass>false</TwoPass>
          <TurboFirstPass>false</TurboFirstPass>
          <Framerate xsi:nil="true" />
          <AudioTracks>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>fdkaac</Encoder>
              <Gain>0</Gain>
              <MixDown>DolbyProLogicII</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>Ac3Passthrough</Encoder>
              <Gain>0</Gain>
              <MixDown>Auto</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
          </AudioTracks>
          <AllowedPassthruOptions>
            <AudioAllowAACPass>true</AudioAllowAACPass>
            <AudioAllowAC3Pass>true</AudioAllowAC3Pass>
            <AudioAllowDTSHDPass>true</AudioAllowDTSHDPass>
            <AudioAllowDTSPass>true</AudioAllowDTSPass>
            <AudioAllowMP3Pass>true</AudioAllowMP3Pass>
            <AudioEncoderFallback>Ac3</AudioEncoderFallback>
          </AllowedPassthruOptions>
          <SubtitleTracks />
          <IncludeChapterMarkers>true</IncludeChapterMarkers>
          <ChapterNames />
          <X264Preset>Slower</X264Preset>
          <QsvPreset>Quality</QsvPreset>
          <H264Profile>High</H264Profile>
          <H264Level>4.1</H264Level>
          <X264Tune>Animation</X264Tune>
          <FastDecode>false</FastDecode>
          <X265Preset>VeryFast</X265Preset>
          <H265Profile>Main</H265Profile>
          <X265Tune>None</X265Tune>
          <PreviewStartAt xsi:nil="true" />
          <PreviewDuration xsi:nil="true" />
          <IsPreviewEncode>false</IsPreviewEncode>
          <PreviewEncodeDuration>0</PreviewEncodeDuration>
          <ShowAdvancedTab>false</ShowAdvancedTab>
        </Task>
        <UsePictureFilters>true</UsePictureFilters>
      </Preset>
      <Preset>
        <Category>User Presets</Category>
        <IsBuildIn>false</IsBuildIn>
        <IsDefault>false</IsDefault>
        <Name>Illig High Profile - HD Grain</Name>
        <PictureSettingsMode>Custom</PictureSettingsMode>
        <UseDeinterlace>false</UseDeinterlace>
        <Task>
          <Title>0</Title>
          <Angle>0</Angle>
          <PointToPointMode>Chapters</PointToPointMode>
          <StartPoint>0</StartPoint>
          <EndPoint>0</EndPoint>
          <OutputFormat>Mp4</OutputFormat>
          <OptimizeMP4>false</OptimizeMP4>
          <IPod5GSupport>false</IPod5GSupport>
          <Width xsi:nil="true" />
          <Height xsi:nil="true" />
          <MaxWidth xsi:nil="true" />
          <MaxHeight xsi:nil="true" />
          <Cropping>
            <Top>0</Top>
            <Bottom>0</Bottom>
            <Left>0</Left>
            <Right>0</Right>
          </Cropping>
          <HasCropping>false</HasCropping>
          <Anamorphic>Loose</Anamorphic>
          <DisplayWidth xsi:nil="true" />
          <KeepDisplayAspect>false</KeepDisplayAspect>
          <PixelAspectX>0</PixelAspectX>
          <PixelAspectY>0</PixelAspectY>
          <Modulus>2</Modulus>
          <Deinterlace>Off</Deinterlace>
          <Decomb>Off</Decomb>
          <Detelecine>Off</Detelecine>
          <Denoise>Off</Denoise>
          <DenoisePreset>Weak</DenoisePreset>
          <DenoiseTune>None</DenoiseTune>
          <Deblock>4</Deblock>
          <Grayscale>false</Grayscale>
          <VideoEncodeRateType>ConstantQuality</VideoEncodeRateType>
          <VideoEncoder>X264</VideoEncoder>
          <FramerateMode>VFR</FramerateMode>
          <Quality>21</Quality>
          <VideoBitrate xsi:nil="true" />
          <TwoPass>false</TwoPass>
          <TurboFirstPass>false</TurboFirstPass>
          <Framerate xsi:nil="true" />
          <AudioTracks>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>fdkaac</Encoder>
              <Gain>0</Gain>
              <MixDown>DolbyProLogicII</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
            <AudioTrack>
              <Bitrate>256</Bitrate>
              <DRC>0</DRC>
              <IsDefault>false</IsDefault>
              <Encoder>Ac3Passthrough</Encoder>
              <Gain>0</Gain>
              <MixDown>Auto</MixDown>
              <SampleRate>0</SampleRate>
              <SampleRateDisplayValue>Auto</SampleRateDisplayValue>
              <ScannedTrack>
                <TrackNumber>0</TrackNumber>
                <SampleRate>0</SampleRate>
                <Bitrate>0</Bitrate>
              </ScannedTrack>
              <TrackName />
            </AudioTrack>
          </AudioTracks>
          <AllowedPassthruOptions>
            <AudioAllowAACPass>true</AudioAllowAACPass>
            <AudioAllowAC3Pass>true</AudioAllowAC3Pass>
            <AudioAllowDTSHDPass>true</AudioAllowDTSHDPass>
            <AudioAllowDTSPass>true</AudioAllowDTSPass>
            <AudioAllowMP3Pass>true</AudioAllowMP3Pass>
            <AudioEncoderFallback>Ac3</AudioEncoderFallback>
          </AllowedPassthruOptions>
          <SubtitleTracks />
          <IncludeChapterMarkers>true</IncludeChapterMarkers>
          <ChapterNames />
          <X264Preset>Slower</X264Preset>
          <QsvPreset>Quality</QsvPreset>
          <H264Profile>High</H264Profile>
          <H264Level>4.1</H264Level>
          <X264Tune>Grain</X264Tune>
          <FastDecode>false</FastDecode>
          <X265Preset>VeryFast</X265Preset>
          <H265Profile>Main</H265Profile>
          <X265Tune>None</X265Tune>
          <PreviewStartAt xsi:nil="true" />
          <PreviewDuration xsi:nil="true" />
          <IsPreviewEncode>false</IsPreviewEncode>
          <PreviewEncodeDuration>0</PreviewEncodeDuration>
          <ShowAdvancedTab>false</ShowAdvancedTab>
        </Task>
        <UsePictureFilters>true</UsePictureFilters>
      </Preset>
    </ArrayOfPreset>
