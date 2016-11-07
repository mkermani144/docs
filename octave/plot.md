Plotting in octave
====

```matlab
% Plot a function (Exponential function here)
x = [0:0.1:4];
y = e.^(x);
plot(x, y);
% Use special color (Red here)
plot(x, y, 'r');
% Label axises
xlabel('Key');
ylabel('Value');
% Add legends
legend('Exponential function');
% Add title
title('Graph of exponential function');
% Change range of axis to show
% Here, show from 1 through 4 in x axis and 0 through 100 in y axis
axis([1 4 0 100]);

% Add another plot on the same open plot other than opening new one
hold on;
y2 = x.^2;
plot(x, y2);
legend('Exponential function', 'Quadratic function');
title('Graph of exponential and quadratic function');

% Make grids in page and draw plots in each grid
% Here, make 2 rows and 1 column and use second grid
subplot(2, 1, 2);
plot(x, y2);
% Use first grid
subplot(2, 1, 1);
plot(x, y, 'r');
% Save as png
print -dpng 'exp.png'

```
