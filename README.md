# 🎬 StreamFlix

Developed StreamFlix, a video streaming platform with storage options on Amazon S3 or on-premise servers, incorporating video encoding and HLS playlist creation via FM Pack. • Implemented DRM security for content protection, utilizing Spring Boot, Spring Data JPA, Docker, MySQL, and React.js for a scalable user experience.
Here's the updated **README.md** for the **StreamFlix** project, now emphasizing the use of **Spring Boot** for development and **Jenkins** for CI/CD:

![StreamFlix-Logo](https://example.com/streamflix-logo.png) <!-- Replace with actual logo URL -->

StreamFlix is a robust video streaming platform that allows users to enjoy a seamless viewing experience. With flexible storage options on **Amazon S3** or on-premise servers, StreamFlix ensures your content is always accessible and secure. The platform incorporates advanced video encoding techniques and HLS playlist creation for optimal streaming performance.

## Features

- 📺 **Dynamic Video Streaming**: Users can watch high-quality videos seamlessly, regardless of their internet connection.
- 🔒 **Content Protection**: Enhanced Digital Rights Management (DRM) security safeguards your valuable content from unauthorized access and piracy.
- ☁️ **Storage Flexibility**: Choose between cloud storage with **Amazon S3** or host your content on your own servers, ensuring flexibility to meet your needs.
- 🖥️ **User-Friendly Interface**: A modern and responsive UI built with **React.js** for an engaging user experience.
- 📈 **Scalable Architecture**: Built with microservices architecture using **Spring Boot** to handle growing user demand effortlessly.

## Technologies Used

### Backend

- **Java** with **Spring Boot**: For building a powerful RESTful API that powers the backend services, enabling rapid development and easy maintenance.
- **Spring Data JPA**: Simplifies database interactions and allows easy integration with **MySQL** for efficient data management.
- **Docker**: Containerizes the application for consistent deployment across various environments.
- **Spring Boot**: For backend development
- **FM Pack**: Utilized for video encoding and creating HLS playlists, ensuring compatibility with various devices.
- **Jenkins**: Automates testing and deployment processes, enabling Continuous Integration and Continuous Deployment (CI/CD) for reliable software delivery.

### Frontend
- **React.js**: Creates a dynamic and responsive user interface that enhances user engagement.
- **HTML5/CSS3**: Standard technologies for structuring and styling the frontend components.

### Storage
- **Amazon S3**: Provides scalable and durable storage for all video content, allowing for efficient data retrieval.
- **On-Premise Servers**: Option to store videos locally for organizations preferring direct control over their content.

---

## Installation and Setup

### Prerequisites

Ensure that you have the following installed:

- **Java 11+** for backend development
- **Node.js** and **npm** for frontend development
- **MySQL** for database management
- **Docker** (if using containerization)
- **Git** for version control

---

## Backend Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/jayram0402/STREAMFLIX.git
   cd streamflix/backend
   ```

2. **Configure MySQL Database**:
   Create a MySQL database and update the connection properties in `application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/streamflixdb
   spring.datasource.username=root
   spring.datasource.password=root
   ```

3. **Build the Backend**:
   Run the following command to build the backend using Maven Wrapper:
   ```bash
   ./mvnw clean install
   ```

4. **Run the Application**:
   Start the Spring Boot application:
   ```bash
   ./mvnw spring-boot:run
   ```

5. **Swagger API Documentation**:
   After starting the backend, visit `http://localhost:8080/swagger-ui.html` for the API documentation and interactive testing.

6. **Optional Docker Setup**:
   To run the backend in a Docker container:
   ```bash
   docker build -t streamflix-backend .
   docker run -p 8080:8080 streamflix-backend
   ```

---

## Frontend Setup

1. **Navigate to the Frontend**:
   ```bash
   cd ../frontend
   ```

2. **Install Dependencies**:
   Run the following command to install all necessary dependencies for the React app:
   ```bash
   npm install
   ```

3. **Configure API Endpoints**:
   Update the API URLs in the React app to point to your backend:
   ```javascript
   const apiUrl = "http://localhost:8080/api";  
   ```

4. **Run the Frontend**:
   Start the development server:
   ```bash
   npm start
   ```
   The frontend will be available at `http://localhost:3000`.

5. **Build for Production**:
   To create a production build, use the following command:
   ```bash
   npm run build
   ```

6. **Optional Docker Setup for Frontend**:
   Build and run the frontend using Docker:
   ```bash
   docker build -t streamflix-frontend .
   docker run -p 3000:3000 streamflix-frontend
   ```

---

## Database Setup

- Use **MySQL** as the primary database to store user data, video metadata, and playlists.
- The database schema is automatically managed by Spring Boot through the `@Entity` annotation in the models.

---

## API Endpoints

Here is a brief list of API endpoints available:

- **POST /api/users**: Register a new user
- **POST /api/videos/upload**: Upload a new video
- **GET /api/videos**: Retrieve a list of all videos
- **GET /api/videos/{id}**: Get details of a specific video
- **POST /api/drm/protect**: Apply DRM protection to uploaded content

You can interact with these endpoints directly or use the **Swagger UI** for testing.

---

## Deployment

### AWS S3 Setup

To deploy your video content to **Amazon S3**:

1. Create an S3 bucket from the AWS Management Console.
2. Configure the bucket permissions to allow public access to videos if needed.
3. Update the `application.properties` file with your S3 bucket details:
   ```properties
   aws.s3.bucket.name=Streamflix
   ```

### AWS EC2 Setup

To deploy the application on an **AWS EC2** instance:

1. **Launch an EC2 Instance**:
   - Go to the **AWS Management Console** and navigate to the **EC2** service.
   - Click on **Launch Instance** and select an Amazon Machine Image (AMI) that suits your needs (e.g., Amazon Linux 2 or Ubuntu).
   - Choose an instance type (e.g., t2.micro for testing).
   - Configure instance details and add storage as needed.

2. **Security Groups**:
   - Create or select a security group that allows inbound traffic on ports **8080** (for backend) and **3000** (for frontend).
   - Ensure SSH (port **22**) is also enabled for remote access.

3. **Connect to the Instance**:
   - Use SSH to connect to your instance:
   ```bash
   ssh -i "your-key.pem" ec2-user@your-public-ip
   ```

4. **Install Required Software**:
   - Install **Java**, **Docker**, and **MySQL** on your EC2 instance. You can use commands like:
   ```bash
   sudo yum update -y
   sudo yum install java-11-openjdk-devel -y
   sudo yum install docker -y
   sudo service docker start
   ```

5. **Deploy the Application**:
   - Clone your repository onto the EC2 instance:
   ```bash
   git clone https://github.com/yourusername/streamflix.git
   cd streamflix
   ```
   - Follow the backend setup instructions to build and run the application.

### CI/CD with Jenkins

Set up a **Jenkins** pipeline that automates testing and deployment to the cloud. Configure your Jenkinsfile to pull from the GitHub repository, build the project with Maven, and deploy to AWS. This ensures that your application is always up to date and minimizes downtime during deployments.

---

## License

This project is licensed under the **MIT License**. See the `LICENSE` file for more details.

---

## Contributing

We welcome contributions! Feel free to submit issues and pull requests for bug fixes, features, and improvements.
