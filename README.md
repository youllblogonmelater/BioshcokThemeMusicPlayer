BioshcokThemeMusicPlayer
========================

Media Player for rainmeter
------------------------------------------
[Rainmeter]
Author=Demented@live.ca

;Metadata added by RainBrowser
;http://rainmeter.net/RainWiki/index.php?title=Rainmeter_101#.5BMetadata.5D

[Metadata]
Name=
Config=
Description=
Instructions=
Version=
Tags=
License=
Variant=
Preview=

;End of added Metadata

[Variables]
color=175, 140, 95, 250
color2=147, 40, 40, 250
graph.line=135, 40, 30, 250
graph.line2=205, 170, 125, 200
font=Peake

------------------------------------------
Measure

[MeasureTrack]
Measure=Plugin
Plugin=NowPlaying
PlayerName=Spotify
PlayerType=TITLE

[MeasureArtist]
Measure=Plugin
Plugin=NowPlaying
PlayerName=Spotify
PlayerType=ARTIST

[MeasureAlbum]
Measure=Plugin
Plugin=NowPlaying
PlayerName=Spotify
PlayerType=ALBUM

[MeasureTime]
Measure=Plugin
Plugin=NowPlaying
PlayerName=Spotify
PlayerType=Position

[MeasureTMinute]
Measure=Calc
Formula=(MeasureTime - (MeasureTime % 60)) /60

[MeasureTSecond]
Measure=Calc
Formula=MeasureTime % 60

[MeasureTZero]
Measure=Calc
Formula=(MeasureTime % 60) < 10 ? 0 : 1
Substitute="1":""

[MeasureProgress]
Measure=Plugin
Plugin=Plugins\iTunesPlugin.dll
Command=GetPlayerPositionPercent
MaxValue=100

[MeasureAlways]
Measure=FreeDiskSpace
Drive=C:
Total=1
MaxValue=1
MinValue=0
UpdateDivider=86400

------------------------------------------
Meters

[iTunesLabel]
Meter=STRING
x=0
y=0
FontColor=#color#
FontFace=#font#
FontSize=12
StringAlign=LEFT
StringStyle=BOLD
AntiAlias=1
Text="Spotify"

[NowPlayingLabel]
Meter=STRING
x=45
y=25
FontColor=#color#
FontFace=#font#
FontSize=7
StringAlign=center
StringStyle=BOLD
AntiAlias=1
Text="-NOW PLAYING-"

[PlayPause]
Meter=Image
ImageName="#CURRENTPATH#\Icons\Songbird.png"
x=12
y=38
LeftMouseUpAction=[!CommandMeasure "MeasureTrack" "PlayPause"]

[Track]
Meter=STRING
MeterStyle=StyleText
MeasureName=MeasureTrack
x=90
y=26
W=290
H=20
ClipString=1
FontColor=#color2#
FontFace=#font#
FontSize=12
StringAlign=LEFT
StringStyle=NORMAL
AntiAlias=1

[Artist]
Meter=STRING
MeasureName=MeasureArtist
Text=--> %1
X=95
Y=44
W=280
H=20
ClipString=1
FontColor=#color2#
FontFace=#font#
FontSize=11
StringAlign=LEFT
StringStyle=NORMAL
AntiAlias=1

------------------------------------------

[Previous]
Meter=STRING
x=100
y=0
FontColor=#color#
FontFace=#font#
FontSize=12
StringAlign=LEFT
StringStyle=BOLD
AntiAlias=1
Text="Previous"
LeftMouseUpAction=[!CommandMeasure "MeasureTrack" "Previous"]

[Next]
Meter=STRING
x=200
y=0
FontColor=#color#
FontFace=#font#
FontSize=12
StringAlign=LEFT
StringStyle=BOLD
AntiAlias=1
Text="Next"
LeftMouseUpAction=[!CommandMeasure "MeasureTrack" "Next"]
