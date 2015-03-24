=========
Handbrake
=========

I use Handbrake to convert my videos into :doc:`MP4 (M4V) format <../../formats/video>`.

SD Settings
===========
My entire ``user_presets.xml`` file is pasted in below, but for readability, I have three SD presets that only differ by the "x264 Tune" setting for Film (most everything), 2D Animation, or Grain.

- Picture

  - Width/Height: nil (let it auto-correct)
  - Anamorphic: Loose
  - Modulus: 2
  - Cropping: Automatic

- Filters

  - Detelecine: Off
  - Decomb: Default
  - Deinterlace: Off
  - Denoise: Off
  - Deblock: Off
  - Grayscale: Unchecked

- Video

  - Video Codec: H.264 (x.264)
  - Framerate FPS: Same as source
  - **Constant Framerate**
  - x264 Preset: Slower
  - x264 Tune: **Film, Animation, or Grain** (depends on the source – I change this per item ripped)
  - H.264 Profile: High
  - H.264 Level: 4.1
  - Fast Decode: Unchecked
  - Extra Options: Empty
  - Quality: **Constant Quality RF 18**

- Audio

  - Track 1:

    - Source: The best AC3 sound track on there with the most channels. (It usually does a good job of auto-detecting.)
    - Codec: **AAC (FDK)**
    - Bitrate: **256**
    - Samplerate: Auto
    - Mixdown: Dolby Pro Logic II
    - DRC: 0.0
    - Gain: 0

  - Track 2:

    - Source: Same as Track 1.
    - Codec: AC3 Passthru

  - Track 3 (depending on source)

    - Source: The DTS track, if there is one.
    - Codec: DTS Passthru

- Subtitles: Generally none, but there are some movies that need them, in which case I'll add one track. High Profile (and my settings) generally don't include this.

  - Source: English (VobSub)
  - Forced Only: Unchecked
  - Burn In: Checked
  - Default: Unchecked
  - Everything else default.

- Chapters: I do select "Create chapter markers" but I let the automatic detection do the naming and timing.

The truly important bits there are **bold** - these are the settings that differ from the "High Profile" preset.

HD Settings
===========
My entire ``user_presets.xml`` file is pasted in below, but for readability, I have three HD presets - one each for Film (most everything), 2D Animation, or Grain.

The settings stem from my SD settings, above, so I'll just put the differences here:

- Filters

  - Decomb: Off

- Video

  - Variable Framerate
  - x264 Tune: Film, Animation, or Grain (depends on the source – I change this per item ripped)
  - Quality:

    - For Film:
    - For Grain: Constant Quality RF 21
    - For Animation:

In testing to find the right HD settings, I went through a few different movies. I found the output size was very different based on the movie type and the x264 Tune setting.

=============  ==============  ==============================  ===================  ==========================
Movie          300             Hunger Games: Mockingjay Pt. I  Across the Universe  Alice in Wonderland (2010)
=============  ==============  ==============================  ===================  ==========================
x264 Tune      Grain           Film                            Film                 Film
Original Size  21,530,308,978  21,742,181,655                  26,831,992,958       24,308,963,706
RF 18          22,119,901,510  --                              --                   --
RF 19          --              3,595,175,689                   11,076,964,804
RF 20          16,703,767,507  3,090,776,234                   8,913,678,948
RF 21          14,317,745,001  2,727,727,566                   7,143,310,965
RF 22          12,158,064,830  --                              --                   --
=============  ==============  ==============================  ===================  ==========================

In particular with *300*, the file was very hard to shrink much because of the details in the grainy appearance. Too much more and you start noticing unfortunate artifacting around edges. The "sweet spot" for me, for grainy movies, seems to be around RF 21 - that's a good balance between file size and quality.

*The Hunger Games: Mockingjay Part I* seemed to create an unusually small file regardless of the RF number. It made me curious why the original was so big. Compared to the other two test movies using the "Film" setting, it definitely seemed to be an outlier. Otherwise, RF 21 seemed to be pretty good in general.

And, of course, these end up being "guidelines" rather than "rules." I start here, and after the conversion I'll see if I need to reconvert with different settings.

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
