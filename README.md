### Technical Highlights
	## Custom WinForms UserControl
A fully reusable station control that can be 
dropped onto any form and configured directly 
from the Visual Studio Property Grid 
no code needed.

	## Precise Session Tracking
Uses a Stopwatch paired with a Timer to track and display session time, 
while recording elapsed seconds separately for accurate billing calculations.
Event-Driven Architecture
When a game finishes, the control raises a custom event passing all session data including time, hourly rate, 
and total fees — keeping it fully decoupled from the rest of the app.

	## Windows Event Viewer Logging
Every completed session is logged with the table name, player name, duration, and timestamp.