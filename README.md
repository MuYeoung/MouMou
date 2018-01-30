# MouMou

PsychDefaultSetup(2);
Screen('Preference', 'SkipSyncTests', 1);

screens = Screen('Screens');
screenNumber = max(screens);

white = WhiteIndex(screenNumber);
black = BlackIndex(screenNumber);

[wPtr, rect] = PsychImaging('OpenWindow', screenNumber, black);

[screenXpixels, screenYpixels] = Screen('WindowSize', wPtr);
[xCenter, yCenter] = RectCenter(rect);

baseRect = [0 0 100 100];

squareXpos = [screenXpixels * 0.15 screenXpixels * 0.25 screenXpixels * 0.35 screenXpixels * 0.45];
squareYpos = [screenYpixels * 0.15 screenYpixels * 0.25 screenYpixels * 0.35 screenYpixels * 0.45];
numSquares = length(squareXpos);

allColors = [1 0 0; 0 1 0; 0 0 1; 1 0 0];


allRects = nan(4, 4);
for i = 1:numSquares
    allRects(:, i) = CenterRectOnPointd(baseRect, squareXpos(i), squareYpos(i));
     
end

Screen('FillRect', wPtr, allColors, allRects);
Screen('Flip', wPtr);

KbWait;
sca;
